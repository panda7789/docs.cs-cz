---
title: Aktivity s regulárními výrazy
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 50daa5b6d7baab37f372de4c30c2e0d12b4fa943
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743161"
---
# <a name="regular-expression-activities"></a><span data-ttu-id="2005f-102">Aktivity s regulárními výrazy</span><span class="sxs-lookup"><span data-stu-id="2005f-102">Regular Expression Activities</span></span>
<span data-ttu-id="2005f-103">Tato ukázka předvádí, jak vytvořit sadu aktivit, které poskytují funkce regulární výraz <xref:System.Text.RegularExpressions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2005f-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="2005f-104">Tyto vlastní aktivity je možné v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2005f-104">These custom activities can be used within a workflow application.</span></span> <span data-ttu-id="2005f-105">Další informace o formátování regulárních výrazů, naleznete v tématu [N:System.Text.RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="2005f-105">For more information about regular expressions, see [N:System.Text.RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="2005f-106">Následující tabulka obsahuje podrobnosti o vlastních aktivit v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="2005f-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="2005f-107">Aktivita</span><span class="sxs-lookup"><span data-stu-id="2005f-107">Activity</span></span>|<span data-ttu-id="2005f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="2005f-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2005f-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="2005f-109">IsMatch</span></span>|<span data-ttu-id="2005f-110">Určuje, zda regulárního výrazu nalezena shoda ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="2005f-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="2005f-111">Shody</span><span class="sxs-lookup"><span data-stu-id="2005f-111">Matches</span></span>|<span data-ttu-id="2005f-112">Vyhledá vstupního řetězce pro všechny výskyty regulárního výrazu a vrátí všechny úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="2005f-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="2005f-113">nahradit</span><span class="sxs-lookup"><span data-stu-id="2005f-113">Replace</span></span>|<span data-ttu-id="2005f-114">V rámci zadaného vstupního řetězce nahradí řetězce, které odpovídají vzoru regulárního výrazu s určeným náhradním.</span><span class="sxs-lookup"><span data-stu-id="2005f-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="2005f-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="2005f-115">IsMatch</span></span>  
 <span data-ttu-id="2005f-116">`IsMatch` Vlastní aktivita vrátí `true` Pokud `Input` vlastnost řetězec najde shodu v regulárním výrazem zadaným v `Pattern` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2005f-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="2005f-117">Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v rámci <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2005f-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="2005f-118">Následující tabulka popisuje vlastnosti a návratová hodnota pro `IsMatch` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="2005f-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="2005f-119">Vlastnost nebo návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2005f-119">Property or Return Value</span></span>|<span data-ttu-id="2005f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2005f-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="2005f-121">Vzor (povinné)</span><span class="sxs-lookup"><span data-stu-id="2005f-121">Pattern (required)</span></span>|<span data-ttu-id="2005f-122">Regulární výraz k vyhledání s.</span><span class="sxs-lookup"><span data-stu-id="2005f-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="2005f-123">Vstup (povinné)</span><span class="sxs-lookup"><span data-stu-id="2005f-123">Input (required)</span></span>|<span data-ttu-id="2005f-124">Vstupní řetězec pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="2005f-124">The input string to search.</span></span>|  
|<span data-ttu-id="2005f-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="2005f-125">RegexOptions</span></span>|<span data-ttu-id="2005f-126">Bitová kombinace OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="2005f-126">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="2005f-127">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2005f-127">Return value</span></span>|<span data-ttu-id="2005f-128">`true` Pokud vstup najde shodu zadaného vzoru; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="2005f-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="2005f-129">Následující příklad kódu ukazuje, jak používat `IsMatch` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="2005f-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="2005f-130">Shody</span><span class="sxs-lookup"><span data-stu-id="2005f-130">Matches</span></span>  
 <span data-ttu-id="2005f-131">`Matches` Vlastní aktivity prohledá vstupní řetězec pro všechny výskyty regulárního výrazu a vrátí všechny úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="2005f-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="2005f-132">Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v rámci <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.Matches%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2005f-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="2005f-133">Následující tabulka popisuje vlastnosti a návratová hodnota pro `IsMatch` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="2005f-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="2005f-134">Vlastnost nebo návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2005f-134">Property or Return Value</span></span>|<span data-ttu-id="2005f-135">Popis</span><span class="sxs-lookup"><span data-stu-id="2005f-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="2005f-136">Vzor (povinné)</span><span class="sxs-lookup"><span data-stu-id="2005f-136">Pattern (required)</span></span>|<span data-ttu-id="2005f-137">Regulární výraz k vyhledání s.</span><span class="sxs-lookup"><span data-stu-id="2005f-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="2005f-138">Vstup (povinné)</span><span class="sxs-lookup"><span data-stu-id="2005f-138">Input (required)</span></span>|<span data-ttu-id="2005f-139">Vstupní řetězec pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="2005f-139">The input string to search.</span></span>|  
|<span data-ttu-id="2005f-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="2005f-140">RegexOptions</span></span>|<span data-ttu-id="2005f-141">Bitová kombinace OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="2005f-141">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="2005f-142">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2005f-142">Return Value</span></span>|<span data-ttu-id="2005f-143">A <xref:System.Text.RegularExpressions.MatchCollection> , který obsahuje kolekci úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="2005f-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="2005f-144">Následující příklad kódu ukazuje, jak používat `Matches` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="2005f-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="2005f-145">nahradit</span><span class="sxs-lookup"><span data-stu-id="2005f-145">Replace</span></span>  
 <span data-ttu-id="2005f-146">`Replace` Vlastní aktivity prohledá vstupní řetězec a nahradí všechny řetězce, které odpovídají zadanému regulárnímu výrazu s řetězcem.</span><span class="sxs-lookup"><span data-stu-id="2005f-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="2005f-147">Aktivita je odvozena z <xref:System.Activities.CodeActivity%601> a v rámci <xref:System.Activities.CodeActivity%601.Execute%2A> volání metod <xref:System.Text.RegularExpressions.Regex.Replace%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2005f-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="2005f-148">Následující tabulka popisuje vlastnosti a návratová hodnota pro `Replace` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="2005f-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="2005f-149">Vlastnost nebo návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2005f-149">Property or Return Value</span></span>|<span data-ttu-id="2005f-150">Popis</span><span class="sxs-lookup"><span data-stu-id="2005f-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="2005f-151">Vzor (povinné)</span><span class="sxs-lookup"><span data-stu-id="2005f-151">Pattern (required)</span></span>|<span data-ttu-id="2005f-152">Regulární výraz k vyhledání s.</span><span class="sxs-lookup"><span data-stu-id="2005f-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="2005f-153">Vstup (povinné)</span><span class="sxs-lookup"><span data-stu-id="2005f-153">Input (required)</span></span>|<span data-ttu-id="2005f-154">Vstupní řetězec pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="2005f-154">The input string to search.</span></span>|  
|<span data-ttu-id="2005f-155">Nahrazení</span><span class="sxs-lookup"><span data-stu-id="2005f-155">Replacement</span></span>|<span data-ttu-id="2005f-156">Náhradní řetězec</span><span class="sxs-lookup"><span data-stu-id="2005f-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="2005f-157">Pokud `Replacement` není zadán, pak bude `MatchEvaluator` vlastnost se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2005f-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="2005f-158">Buď `Replacement` nebo `MatchEvaluator` musí být nastavena vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2005f-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="2005f-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="2005f-159">MatchEvaluator</span></span>|<span data-ttu-id="2005f-160">Vlastní metoda, která zkontroluje jednotlivých shod a vrátí původní odpovídající řetězec nebo řetězec nahrazení.</span><span class="sxs-lookup"><span data-stu-id="2005f-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="2005f-161">Pokud `Replacement` není zadán, pak bude `MatchEvaluator` vlastnost se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2005f-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="2005f-162">Buď `Replacement` nebo `MatchEvaluator` musí být nastavena vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2005f-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="2005f-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="2005f-163">RegexOptions</span></span>|<span data-ttu-id="2005f-164">Bitová kombinace OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="2005f-164">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="2005f-165">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2005f-165">Return Value</span></span>|<span data-ttu-id="2005f-166">A <xref:System.Text.RegularExpressions.MatchCollection> , který obsahuje kolekci úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="2005f-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="2005f-167">Následující příklad kódu ukazuje, jak používat `Replace` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="2005f-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2005f-168">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="2005f-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="2005f-169">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RegexActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="2005f-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2005f-170">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2005f-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2005f-171">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="2005f-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2005f-172">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="2005f-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2005f-173">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2005f-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2005f-174">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2005f-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2005f-175">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2005f-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`