---
title: Vlastní aktivita pro přepnutí u rozsahu hodnot
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: cfaf4318b1557a9fc217de8254e164243ea54569
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066997"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>Vlastní aktivita pro přepnutí u rozsahu hodnot
Tato ukázka předvádí, jak vytvořit vlastní aktivitu, která rozšiřuje použití <xref:System.Activities.Statements.Switch%601>. Konvenční <xref:System.Activities.Statements.Switch%601> příkaz umožňuje přechod na základě jedné hodnoty. Existují ale obchodní scénáře, kde musíte přepnout aktivity na základě rozsahu hodnot. Aktivita může například spustit jednu akci, pokud je hodnota přepnut na 1 až 5, další akci, pokud je hodnota délku 6 až 10 a výchozí akce pro všechny ostatní hodnoty. Tato vlastní aktivita umožňuje přesně tento scénář.  
  
## <a name="the-switchrange-activity"></a>Aktivita SwitchRange  
 `SwitchRange` Aktivity naplánuje podřízené aktivity, když výsledek hodnotu jeho výrazu je součástí rozsahu jednoho z jeho `Cases`.  
  
 Následující příklad kódu je vlastní aktivitu, která přepínače na základě rozsahu hodnot.  
  
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
|Výraz|Toto je výraz, který má být vyhodnocen a porovnáván proti oblasti v seznamu případy. Výsledek výrazu je typu T.|  
|Případy|Každý případ se skládá z rozsahu (od a do) a aktivita (text). Výraz je vyhodnocen a porovnáván proti rozsahů. Pokud je výsledkem výrazu v rozsahu jedním z případů, bude odpovídající aktivita je provedena.|  
|Výchozí|Aktivity, který je proveden, pokud žádný případ je nalezena shoda. Pokud je nastavena na `null`, nebyla provedena žádná akce.|  
  
## <a name="caserange-class"></a>Třída CaseRange  
 `CaseRange` Třída reprezentuje rozsah v rámci `SwitchRange` aktivity. Každou instanci `CaseRange` obsahuje rozsah (tvořený `From` a `To`) a `Body` aktivitu, která je naplánováno, pokud výraz v `SwitchRange` vyhodnotí v rámci rozsahu.  
  
 Následující příklad kódu je definice `CaseRange` třídy.  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  Jak `SwitchRange` a `CaseRange` třídy, které jsou definovány v ukázce jsou obecné třídy, které budou fungovat s jakýmkoli typem, který implementuje `IComparable`, třeba <xref:System.Activities.Statements.Switch%601> třídy.  
  
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
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`