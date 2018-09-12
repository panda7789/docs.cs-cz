---
title: Expressions2
ms.date: 03/30/2017
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
ms.openlocfilehash: e852b62e6d0b6b4b3ddc19b197902de5325310a1
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44493535"
---
# <a name="expressions"></a>Výrazy
Tento příklad ukazuje, jak používat základní výrazy v pracovním postupu. Skládá se z pracovní postup, který vypočítá základní salary statistiky pro dva zaměstnance fiktivní společnosti. Dvě třídy `Employee` a `SalaryStats`, jsou definovány v Employee.cs a SalaryStats.cs. Tyto třídy se používají v pracovním postupu, který ukazuje, jak provádět jednoduché řetězec a aritmetické operace na vlastnosti proměnných komplexních typů.  
  
 Pracovní postup salary výpočtu je definována v XAML i v jazyce C# k předvedení dva styly pro vytváření obsahu. Verze XAML je součástí SalaryCalculation.xaml a můžete být zobrazit a upravit v Návrháři pracovních postupů. Verze jazyka C# je umístěn v souboru Program.cs. Výrazy použité v XAML v souladu s syntaxe jazyka Visual Basic a použít <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> aktivity výrazů. Další informace o jazyce Visual Basic výrazů naleznete v tématu [výrazy jazyka Visual Basic](https://go.microsoft.com/fwlink/?LinkId=165912). Na druhé straně, se zapisují jako výrazy lambda výrazy v jazyce C# a použijte <xref:System.Activities.Expressions.LambdaValue%601> a <xref:System.Activities.Expressions.LambdaReference%601> aktivity výrazů. Zápis výrazů jako výrazy lambda umožňuje kompilátoru C# pro poskytuje zvýraznění syntaxe a statické ověření. Další informace o výrazech lambda v jazyce C# najdete v tématu [výrazy Lambda (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=182082). Pokud pracovní postup se vytváří v kódu jazyka Visual Basic, se používají výrazy lambda v jazyce Visual Basic. Další informace o výrazech lambda v jazyce Visual Basic najdete v tématu [výrazy Lambda (Visual Basic)](https://go.microsoft.com/fwlink/?LinkId=152437). Další informace o vytváření pracovních postupů pomocí kódu, naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení Expressions.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B pro vytvoření řešení, nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
    > [!NOTE]
    >  Otevřete SalaryCalculation.xaml v návrháři aplikace Visual Studio, musíte nejprve zkompilovat váš projekt a zkontrolujte, že `Employee` a `SalaryStats` třídy jsou k dispozici do návrháře.  
  
3.  Po sestavení byla úspěšná, stiskněte klávesu F5 nebo vyberte **spustit ladění** z **ladění** nabídky. Případně můžete stisknutím kláves Ctrl + F5 nebo vyberte **spustit bez ladění** z **ladění** nabídky spustit bez ladění.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`