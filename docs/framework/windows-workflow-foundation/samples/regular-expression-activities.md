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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c04b5c97feb7843a5120e3b2171e132526caa961
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="regular-expression-activities"></a><span data-ttu-id="946d5-102">Regulární výraz aktivity</span><span class="sxs-lookup"><span data-stu-id="946d5-102">Regular Expression Activities</span></span>
<span data-ttu-id="946d5-103">Tento příklad ukazuje, jak vytvořit sadu aktivit, které poskytují funkce regulární výraz <xref:System.Text.RegularExpressions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="946d5-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="946d5-104">Tyto vlastní aktivity lze použít v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="946d5-104">These custom activities can be used within a workflow application.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="946d5-105">regulární výrazy, najdete v části [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="946d5-105"> regular expressions, see [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="946d5-106">V následující tabulce jsou vlastní aktivity v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="946d5-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="946d5-107">Aktivita</span><span class="sxs-lookup"><span data-stu-id="946d5-107">Activity</span></span>|<span data-ttu-id="946d5-108">Popis</span><span class="sxs-lookup"><span data-stu-id="946d5-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="946d5-109">IsMatch –</span><span class="sxs-lookup"><span data-stu-id="946d5-109">IsMatch</span></span>|<span data-ttu-id="946d5-110">Určuje, zda regulární výraz nalezena shoda ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="946d5-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="946d5-111">Shody</span><span class="sxs-lookup"><span data-stu-id="946d5-111">Matches</span></span>|<span data-ttu-id="946d5-112">Prohledá vstupní řetězec pro všechny výskyty regulární výraz a vrátí všechny úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="946d5-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="946d5-113">Nahradit</span><span class="sxs-lookup"><span data-stu-id="946d5-113">Replace</span></span>|<span data-ttu-id="946d5-114">V rámci vstupní řetězec nahradí řetězce, které odpovídají vzor regulárního výrazu s zadané náhradní řetězec.</span><span class="sxs-lookup"><span data-stu-id="946d5-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="946d5-115">IsMatch –</span><span class="sxs-lookup"><span data-stu-id="946d5-115">IsMatch</span></span>  
 <span data-ttu-id="946d5-116">`IsMatch` Vlastní aktivita vrátí `true` Pokud `Input` vlastnost řetězec najde shoda v regulárním výrazem zadaným v `Pattern` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="946d5-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="946d5-117">Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="946d5-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="946d5-118">Následující tabulka popisuje hodnota vlastnosti a vraťte se `IsMatch` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="946d5-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="946d5-119">Vlastnost nebo vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="946d5-119">Property or Return Value</span></span>|<span data-ttu-id="946d5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="946d5-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="946d5-121">Vzor (povinné)</span><span class="sxs-lookup"><span data-stu-id="946d5-121">Pattern (required)</span></span>|<span data-ttu-id="946d5-122">Regulární výraz k vyhledání s.</span><span class="sxs-lookup"><span data-stu-id="946d5-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="946d5-123">Vstup (povinné)</span><span class="sxs-lookup"><span data-stu-id="946d5-123">Input (required)</span></span>|<span data-ttu-id="946d5-124">Vstupní řetězec pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="946d5-124">The input string to search.</span></span>|  
|<span data-ttu-id="946d5-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="946d5-125">RegexOptions</span></span>|<span data-ttu-id="946d5-126">Bitová kombinace OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="946d5-126">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="946d5-127">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="946d5-127">Return value</span></span>|<span data-ttu-id="946d5-128">`true`Pokud vstupní najde shoda v zadaný vzor; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="946d5-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="946d5-129">Následující příklad kódu ukazuje, jak používat `IsMatch` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="946d5-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="946d5-130">Shody</span><span class="sxs-lookup"><span data-stu-id="946d5-130">Matches</span></span>  
 <span data-ttu-id="946d5-131">`Matches` Vlastní aktivity prohledá vstupní řetězec pro všechny výskyty regulární výraz a vrátí všechny úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="946d5-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="946d5-132">Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.Matches%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="946d5-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="946d5-133">Následující tabulka popisuje hodnota vlastnosti a vraťte se `IsMatch` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="946d5-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="946d5-134">Vlastnost nebo vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="946d5-134">Property or Return Value</span></span>|<span data-ttu-id="946d5-135">Popis</span><span class="sxs-lookup"><span data-stu-id="946d5-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="946d5-136">Vzor (povinné)</span><span class="sxs-lookup"><span data-stu-id="946d5-136">Pattern (required)</span></span>|<span data-ttu-id="946d5-137">Regulární výraz k vyhledání s.</span><span class="sxs-lookup"><span data-stu-id="946d5-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="946d5-138">Vstup (povinné)</span><span class="sxs-lookup"><span data-stu-id="946d5-138">Input (required)</span></span>|<span data-ttu-id="946d5-139">Vstupní řetězec pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="946d5-139">The input string to search.</span></span>|  
|<span data-ttu-id="946d5-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="946d5-140">RegexOptions</span></span>|<span data-ttu-id="946d5-141">Bitová kombinace OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="946d5-141">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="946d5-142">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="946d5-142">Return Value</span></span>|<span data-ttu-id="946d5-143">A <xref:System.Text.RegularExpressions.MatchCollection> obsahující kolekce shod úspěšné.</span><span class="sxs-lookup"><span data-stu-id="946d5-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="946d5-144">Následující příklad kódu ukazuje, jak používat `Matches` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="946d5-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="946d5-145">Nahradit</span><span class="sxs-lookup"><span data-stu-id="946d5-145">Replace</span></span>  
 <span data-ttu-id="946d5-146">`Replace` Vlastní aktivity prohledá vstupní řetězec a nahradí všechny řetězce, které odpovídají zadanému regulárnímu výrazu řetězcem.</span><span class="sxs-lookup"><span data-stu-id="946d5-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="946d5-147">Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.Replace%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="946d5-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="946d5-148">Následující tabulka popisuje hodnota vlastnosti a vraťte se `Replace` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="946d5-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="946d5-149">Vlastnost nebo vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="946d5-149">Property or Return Value</span></span>|<span data-ttu-id="946d5-150">Popis</span><span class="sxs-lookup"><span data-stu-id="946d5-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="946d5-151">Vzor (povinné)</span><span class="sxs-lookup"><span data-stu-id="946d5-151">Pattern (required)</span></span>|<span data-ttu-id="946d5-152">Regulární výraz k vyhledání s.</span><span class="sxs-lookup"><span data-stu-id="946d5-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="946d5-153">Vstup (povinné)</span><span class="sxs-lookup"><span data-stu-id="946d5-153">Input (required)</span></span>|<span data-ttu-id="946d5-154">Vstupní řetězec pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="946d5-154">The input string to search.</span></span>|  
|<span data-ttu-id="946d5-155">Nahrazení</span><span class="sxs-lookup"><span data-stu-id="946d5-155">Replacement</span></span>|<span data-ttu-id="946d5-156">Náhradní řetězec</span><span class="sxs-lookup"><span data-stu-id="946d5-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="946d5-157">Pokud `Replacement` není zadaný, pak se `MatchEvaluator` vlastnost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="946d5-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="946d5-158">Buď `Replacement` nebo `MatchEvaluator` musí být nastavena vlastnost.</span><span class="sxs-lookup"><span data-stu-id="946d5-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="946d5-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="946d5-159">MatchEvaluator</span></span>|<span data-ttu-id="946d5-160">Vlastní metodu, která hledá každé shody a vrátí původní odpovídající řetězec nebo řetězec nahrazení.</span><span class="sxs-lookup"><span data-stu-id="946d5-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="946d5-161">Pokud `Replacement` není zadaný, pak se `MatchEvaluator` vlastnost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="946d5-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="946d5-162">Buď `Replacement` nebo `MatchEvaluator` musí být nastavena vlastnost.</span><span class="sxs-lookup"><span data-stu-id="946d5-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="946d5-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="946d5-163">RegexOptions</span></span>|<span data-ttu-id="946d5-164">Bitová kombinace OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="946d5-164">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="946d5-165">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="946d5-165">Return Value</span></span>|<span data-ttu-id="946d5-166">A <xref:System.Text.RegularExpressions.MatchCollection> obsahující kolekce shod úspěšné.</span><span class="sxs-lookup"><span data-stu-id="946d5-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="946d5-167">Následující příklad kódu ukazuje, jak používat `Replace` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="946d5-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="946d5-168">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="946d5-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="946d5-169">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RegexActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="946d5-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="946d5-170">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="946d5-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="946d5-171">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="946d5-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="946d5-172">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="946d5-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="946d5-173">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="946d5-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="946d5-174">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="946d5-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="946d5-175">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="946d5-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`