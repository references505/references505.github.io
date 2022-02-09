var currentRootItem=null;
var rootLevel=null;
function onclickMenu(item){	
	if(item.getAttribute('level')==rootLevel){		
		if(currentRootItem!=null){			
			if(currentRootItem!=item){				
				if(currentRootItem.nextSibling!=null){					
					currentRootItem.nextSibling.style.display='none';					
				}				
				currentRootItem.className='';					
			}			
		}
		currentRootItem=item;				
	}
	item.className='level'+item.getAttribute('level')+'_selected';
	if(item.nextSibling!=null){		
		if(item.nextSibling.style.display=='none'){			
			item.nextSibling.style.display='';
			item.className='level'+item.getAttribute('level')+'_withsubselected';			
		}
		else {			
			item.nextSibling.style.display='none';			
			item.className='';
		}		
	}
}
function initTabs(){
	var curTabId = -1;
	var reg = new RegExp("tabid[\/=]+(\\d+)|\/tab(\\d+)\/","ig");
	var vAddress = document.forms[0].action;
	if(reg.exec(vAddress)!=null){
	if(RegExp.$1.length>0)
		curTabId = parseInt(RegExp.$1);
	else
		curTabId = parseInt(RegExp.$2);
	}
	var divNav = document.getElementById('XMLNav');
	var eles = divNav.getElementsByTagName('A');
	for(i=0;i < eles.length;i++){
		var varA = eles[i];
		//first A is the root item
		if(i==0) rootLevel = varA.getAttribute('level');
		if(varA.getAttribute('level')==rootLevel){
			varA.parentNode.parentNode.style.display='';
		}
		if(varA.nextSibling!=null){ varA.className='level' + varA.getAttribute('level')+'_withsub';}		
		if(varA.getAttribute('tabid')==curTabId){
			expandTabRecursed(varA);			
		}		
	}
}
function expandTabRecursed(item){
	item.className='level'+item.getAttribute('level')+'_selected';
	if(item.nextSibling!=null){		
		if(item.nextSibling.style.display=='none'){			
			item.nextSibling.style.display='';
		}
		item.className='level'+item.getAttribute('level')+'_withsubselected';
	}
	if(item.getAttribute('level')==rootLevel) {currentRootItem=item;return;}
	expandTabRecursed(item.parentNode.parentNode.previousSibling);
}