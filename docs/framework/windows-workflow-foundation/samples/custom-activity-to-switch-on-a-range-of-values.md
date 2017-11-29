---
title: "Vlastní aktivity k přepínači na rozsahu hodnot"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2f422c4001c2e6ec46fc796e8dbf1b85e6a2b77
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>Vlastní aktivity k přepínači na rozsahu hodnot
Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která rozšiřuje použití <xref:System.Activities.Statements.Switch%601>. Konvenční <xref:System.Activities.Statements.Switch%601> příkaz umožňuje přepnutí na základě jednu hodnotu. Ale existují obchodní scénáře, kde musí přejít aktivitu na základě rozsahu hodnot. Například aktivita může provést jednu akci, pokud je hodnota přepnut na 1 až 5, další akci, pokud je hodnota 6 až 10 a výchozí akce pro všechny ostatní hodnoty. Tato vlastní aktivita umožňuje přesně tento scénář.  
  
## <a name="the-switchrange-activity"></a>SwitchRange aktivity  
 `SwitchRange` Aktivity plány podřízené aktivity, pokud je hodnota výsledek jejího výrazu zahrnuté v rozsahu mezi jeho `Cases`.  
  
 Následující příklad kódu je vlastní aktivity, které přepínače na základě rozsahu hodnot.  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|Vlastnost|Popis|  
|-|-|  
|Výraz|Toto je výraz, který se vyhodnotí a porovná s rozsahy v seznamu případů. Výsledkem výrazu je typu T.|  
|Případy|Každý případ se skládá z rozsah (od a do) a aktivitu (text). Výraz je vyhodnocena a porovná s rozsahy. Pokud je výsledek výrazu v rozsahu mezi v případech, bude odpovídající aktivita se spustí.|  
|Výchozí|Aktivita, která se spustí, pokud je nalezena shoda s žádné případu. Pokud nastavíte hodnotu `null`, nebyla provedena žádná akce.|  
  
## <a name="caserange-class"></a>CaseRange – třída  
 `CaseRange` Třída reprezentuje rozsahem v rámci `SwitchRange` aktivity. Všechny instance řetězce `CaseRange` obsahuje rozsah (tvořený `From` a `To`) a `Body` aktivity, která je naplánováno, pokud výraz ve `SwitchRange` vyhodnotí v rámci rozsahu.  
  
 Následující příklad kódu je definice pro `CaseRange` třídy.  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  Jak `SwitchRange` a `CaseRange` třídy, které jsou definovány v ukázce jsou obecné třídy, které můžete pracovat s žádným typem, který implementuje `IComparable`, například <xref:System.Activities.Statements.Switch%601> třídy.  
  
## <a name="sample-usage"></a>Využití vzorků  
 Následující příklad kódu ukazuje, jak používat `SwitchRange` aktivity.  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení SwitchRange.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`  
  
## <a name="see-also"></a>Viz také
