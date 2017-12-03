---
title: "Regulární výraz aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77968872d878f7b4d6b0eb3f27516a75abb54919
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="regular-expression-activities"></a>Regulární výraz aktivity
Tento příklad ukazuje, jak vytvořit sadu aktivit, které poskytují funkce regulární výraz <xref:System.Text.RegularExpressions> oboru názvů. Tyto vlastní aktivity lze použít v rámci aplikace pracovního postupu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]regulární výrazy, najdete v části [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.  
  
 V následující tabulce jsou vlastní aktivity v této ukázce.  
  
|Aktivita|Popis|  
|--------------|-----------------|  
|IsMatch –|Určuje, zda regulární výraz nalezena shoda ve vstupním řetězci.|  
|Shody|Prohledá vstupní řetězec pro všechny výskyty regulární výraz a vrátí všechny úspěšné shody.|  
|Nahradit|V rámci vstupní řetězec nahradí řetězce, které odpovídají vzor regulárního výrazu s zadané náhradní řetězec.|  
  
## <a name="ismatch"></a>IsMatch –  
 `IsMatch` Vlastní aktivita vrátí `true` Pokud `Input` vlastnost řetězec najde shoda v regulárním výrazem zadaným v `Pattern` vlastnost. Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda.  
  
 Následující tabulka popisuje hodnota vlastnosti a vraťte se `IsMatch` vlastní aktivity.  
  
|Vlastnost nebo vrací hodnotu|Popis|  
|------------------------------|-----------------|  
|Vzor (povinné)|Regulární výraz k vyhledání s.|  
|Vstup (povinné)|Vstupní řetězec pro vyhledávání.|  
|RegexOptions|Bitová kombinace OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.|  
|Návratová hodnota|`true`Pokud vstupní najde shoda v zadaný vzor; v opačném případě `false`.|  
  
 Následující příklad kódu ukazuje, jak používat `IsMatch` vlastní aktivity.  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a>Shody  
 `Matches` Vlastní aktivity prohledá vstupní řetězec pro všechny výskyty regulární výraz a vrátí všechny úspěšné shody. Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.Matches%2A> metoda.  
  
 Následující tabulka popisuje hodnota vlastnosti a vraťte se `IsMatch` vlastní aktivity.  
  
|Vlastnost nebo vrací hodnotu|Popis|  
|------------------------------|-----------------|  
|Vzor (povinné)|Regulární výraz k vyhledání s.|  
|Vstup (povinné)|Vstupní řetězec pro vyhledávání.|  
|RegexOptions|Bitová kombinace OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.|  
|Návratová hodnota|A <xref:System.Text.RegularExpressions.MatchCollection> obsahující kolekce shod úspěšné.|  
  
 Následující příklad kódu ukazuje, jak používat `Matches` vlastní aktivity.  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a>Nahradit  
 `Replace` Vlastní aktivity prohledá vstupní řetězec a nahradí všechny řetězce, které odpovídají zadanému regulárnímu výrazu řetězcem. Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.Replace%2A> metoda.  
  
 Následující tabulka popisuje hodnota vlastnosti a vraťte se `Replace` vlastní aktivity.  
  
|Vlastnost nebo vrací hodnotu|Popis|  
|------------------------------|-----------------|  
|Vzor (povinné)|Regulární výraz k vyhledání s.|  
|Vstup (povinné)|Vstupní řetězec pro vyhledávání.|  
|Nahrazení|Náhradní řetězec<br /><br /> Pokud `Replacement` není zadaný, pak se `MatchEvaluator` vlastnost je ignorována. Buď `Replacement` nebo `MatchEvaluator` musí být nastavena vlastnost.|  
|MatchEvaluator|Vlastní metodu, která hledá každé shody a vrátí původní odpovídající řetězec nebo řetězec nahrazení.<br /><br /> Pokud `Replacement` není zadaný, pak se `MatchEvaluator` vlastnost je ignorována. Buď `Replacement` nebo `MatchEvaluator` musí být nastavena vlastnost.|  
|RegexOptions|Bitová kombinace OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.|  
|Návratová hodnota|A <xref:System.Text.RegularExpressions.MatchCollection> obsahující kolekce shod úspěšné.|  
  
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
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`