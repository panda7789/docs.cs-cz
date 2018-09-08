---
title: Aktivity s regulárními výrazy
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 50daa5b6d7baab37f372de4c30c2e0d12b4fa943
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201007"
---
# <a name="regular-expression-activities"></a>Aktivity s regulárními výrazy
Tato ukázka předvádí, jak vytvořit sadu aktivit, které poskytují funkce regulární výraz <xref:System.Text.RegularExpressions> oboru názvů. Tyto vlastní aktivity je možné v rámci aplikace pracovního postupu. Další informace o formátování regulárních výrazů, naleznete v tématu [N:System.Text.RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.  
  
 Následující tabulka obsahuje podrobnosti o vlastních aktivit v této ukázce.  
  
|Aktivita|Popis|  
|--------------|-----------------|  
|IsMatch|Určuje, zda regulárního výrazu nalezena shoda ve vstupním řetězci.|  
|Shody|Vyhledá vstupního řetězce pro všechny výskyty regulárního výrazu a vrátí všechny úspěšné shody.|  
|nahradit|V rámci zadaného vstupního řetězce nahradí řetězce, které odpovídají vzoru regulárního výrazu s určeným náhradním.|  
  
## <a name="ismatch"></a>IsMatch  
 `IsMatch` Vlastní aktivita vrátí `true` Pokud `Input` vlastnost řetězec najde shodu v regulárním výrazem zadaným v `Pattern` vlastnost. Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v rámci <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda.  
  
 Následující tabulka popisuje vlastnosti a návratová hodnota pro `IsMatch` vlastní aktivity.  
  
|Vlastnost nebo návratová hodnota|Popis|  
|------------------------------|-----------------|  
|Vzor (povinné)|Regulární výraz k vyhledání s.|  
|Vstup (povinné)|Vstupní řetězec pro vyhledávání.|  
|RegexOptions|Bitová kombinace OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.|  
|Návratová hodnota|`true` Pokud vstup najde shodu zadaného vzoru; v opačném případě `false`.|  
  
 Následující příklad kódu ukazuje, jak používat `IsMatch` vlastní aktivity.  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a>Shody  
 `Matches` Vlastní aktivity prohledá vstupní řetězec pro všechny výskyty regulárního výrazu a vrátí všechny úspěšné shody. Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v rámci <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.Matches%2A> metoda.  
  
 Následující tabulka popisuje vlastnosti a návratová hodnota pro `IsMatch` vlastní aktivity.  
  
|Vlastnost nebo návratová hodnota|Popis|  
|------------------------------|-----------------|  
|Vzor (povinné)|Regulární výraz k vyhledání s.|  
|Vstup (povinné)|Vstupní řetězec pro vyhledávání.|  
|RegexOptions|Bitová kombinace OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.|  
|Návratová hodnota|A <xref:System.Text.RegularExpressions.MatchCollection> , který obsahuje kolekci úspěšné shody.|  
  
 Následující příklad kódu ukazuje, jak používat `Matches` vlastní aktivity.  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a>nahradit  
 `Replace` Vlastní aktivity prohledá vstupní řetězec a nahradí všechny řetězce, které odpovídají zadanému regulárnímu výrazu s řetězcem. Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v rámci <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.Replace%2A> metoda.  
  
 Následující tabulka popisuje vlastnosti a návratová hodnota pro `Replace` vlastní aktivity.  
  
|Vlastnost nebo návratová hodnota|Popis|  
|------------------------------|-----------------|  
|Vzor (povinné)|Regulární výraz k vyhledání s.|  
|Vstup (povinné)|Vstupní řetězec pro vyhledávání.|  
|Nahrazení|Náhradní řetězec<br /><br /> Pokud `Replacement` není zadán, pak bude `MatchEvaluator` vlastnost se ignoruje. Buď `Replacement` nebo `MatchEvaluator` musí být nastavena vlastnost.|  
|MatchEvaluator|Vlastní metoda, která zkontroluje jednotlivých shod a vrátí původní odpovídající řetězec nebo řetězec nahrazení.<br /><br /> Pokud `Replacement` není zadán, pak bude `MatchEvaluator` vlastnost se ignoruje. Buď `Replacement` nebo `MatchEvaluator` musí být nastavena vlastnost.|  
|RegexOptions|Bitová kombinace OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.|  
|Návratová hodnota|A <xref:System.Text.RegularExpressions.MatchCollection> , který obsahuje kolekci úspěšné shody.|  
  
 Následující příklad kódu ukazuje, jak používat `Replace` vlastní aktivity.  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RegexActivities.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`