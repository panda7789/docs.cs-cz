---
title: "Pomocí aktivity InvokeMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aacc20bf483877ac501fd8b35c04f6e3f9311afb
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-invokemethod-activity"></a>Pomocí aktivity InvokeMethod
Tento příklad znázorňuje způsob použití <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) aktivity k vyvolání veřejné metody ve veřejné třídy. <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) Aktivita povoluje pracovního postupu k volání metody u objektů, předat parametry, získat návratovou hodnotu, určit typy pro obecné metody a určete, zda je metoda synchronní nebo asynchronní. 
  
Je neobecnou verzi <xref:System.Activities.Statements.InvokeMethod> aktivity, kde je návratovou hodnotu nastaven na <xref:System.Activities.Statements.InvokeMethod.Result%2A> vlastnost a obecná verze <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) aktivity, kde se vrátí návratová hodnota prostřednictvím <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) vlastnost typu `TResult`. 
  
 Tento příklad ukazuje způsob volání různé typy metoda. Následující podrobnosti seznam typů metoda předvedená v této ukázce:  
  
-   Vyvolání metody instance bez parametrů.  
  
-   Vyvolání metody instance s dva parametry (System.String a System.Int32).  
  
-   Vyvolání metody instance s dva parametry (System.String a System.Int32) a parametr pole typu System.String [].  
  
-   Vyvolání metody instance s dva parametry (dvou čísel System.Int32) a výsledek typu System.Int32.  
  
     Návratová hodnota je vázán k proměnné a vytisknout pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.  
  
-   Vyvolání statickou metodu s dva parametry (System.String a System.Int32).  
  
-   Vyvolání metody instance s jeden obecný parametr (System.String).  
  
-   Vyvolání statickou metodu s dvě obecné parametry (System.String a System.Int32).  
  
-   Vyvolání metody instance, který má jeden parametr předaný odkazem (System.String).  
  
     Parametr odkazované je vázán k proměnné a vytisknout pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.  
  
-   Vyvolání metody asynchronní instance.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`