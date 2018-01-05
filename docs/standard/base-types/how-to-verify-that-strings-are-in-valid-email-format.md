---
title: "Postupy: Ověření platnosti e-mailového formátu řetězců"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, e-mail strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- e-mail [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
caps.latest.revision: "30"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 376acbeb09519f0b4724c659984dccab81f4a0f6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="1d9b8-102">Postupy: Ověření platnosti e-mailového formátu řetězců</span><span class="sxs-lookup"><span data-stu-id="1d9b8-102">How to: Verify that Strings Are in Valid Email Format</span></span>
<span data-ttu-id="1d9b8-103">Následující příklad používá regulární výraz k ověření, že je řetězec ve formátu platné e-mailu.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-103">The following example uses a regular expression to verify that a string is in valid email format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d9b8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d9b8-104">Example</span></span>  
 <span data-ttu-id="1d9b8-105">V příkladu je definován `IsValidEmail` metoda, která vrátí `true` Pokud řetězec obsahuje platnou e-mailovou adresu a `false` Pokud ne, ale žádné další akce.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-105">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it does not, but takes no other action.</span></span>  
  
 <span data-ttu-id="1d9b8-106">Chcete-li ověřit, že e-mailová adresa je platná, `IsValidEmail` volání metod <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metoda s `(@)(.+)$` vzor regulárního výrazu nezávislá na název domény e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-106">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="1d9b8-107">Třetí parametr není <xref:System.Text.RegularExpressions.MatchEvaluator> delegáta, který představuje metodu, která zpracovává a nahradí odpovídající text.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-107">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="1d9b8-108">Regulární výraz interpretována následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-108">The regular expression pattern is interpreted as follows.</span></span>  
  
|<span data-ttu-id="1d9b8-109">Vzor</span><span class="sxs-lookup"><span data-stu-id="1d9b8-109">Pattern</span></span>|<span data-ttu-id="1d9b8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1d9b8-110">Description</span></span>|  
|-------------|-----------------|  
|`(@)`|<span data-ttu-id="1d9b8-111">Shoda znak @.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-111">Match the @ character.</span></span> <span data-ttu-id="1d9b8-112">Toto je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-112">This is the first capturing group.</span></span>|  
|`(.+)`|<span data-ttu-id="1d9b8-113">Porovná jeden nebo více výskytů libovolného znaku.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-113">Match one or more occurrences of any character.</span></span> <span data-ttu-id="1d9b8-114">Toto je druhá zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-114">This is the second capturing group.</span></span>|  
|`$`|<span data-ttu-id="1d9b8-115">Ukončí porovnávání na konci řetězce.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-115">End the match at the end of the string.</span></span>|  
  
 <span data-ttu-id="1d9b8-116">Název domény spolu s znak @ je předán `DomainMapper` metoda, která používá <xref:System.Globalization.IdnMapping> třída přeložit znaky znakové sady Unicode, které jsou mimo rozsah znaků US-ASCII na kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-116">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="1d9b8-117">Metoda také nastaví `invalid` příznak, který `True` Pokud <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> metoda zjistí žádné neplatné znaky v názvu domény.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-117">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="1d9b8-118">Metoda vrátí název domény Punycode předchází @ symbol, který má `IsValidEmail` metoda.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-118">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>  
  
 <span data-ttu-id="1d9b8-119">`IsValidEmail` Metoda pak zavolá <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodu k ověření, že adresa odpovídá regulárnímu výrazu.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-119">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>  
  
 <span data-ttu-id="1d9b8-120">Všimněte si, že `IsValidEmail` metoda neprovádí ověřování k ověření e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-120">Note that the `IsValidEmail` method does not perform authentication to validate the email address.</span></span> <span data-ttu-id="1d9b8-121">Jenom Určuje, zda je formát platný pro e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-121">It merely determines whether its format is valid for an email address.</span></span> <span data-ttu-id="1d9b8-122">Kromě toho `IsValidEmail` metoda neověřuje, zda je název domény nejvyšší úrovně platný název domény uvedený na [IANA kořenová zóna databáze](https://www.iana.org/domains/root/db), které by vyžadovaly operace hledání.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-122">In addition, the `IsValidEmail` method does not verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span> <span data-ttu-id="1d9b8-123">Regulární výraz místo toho jenom ověřuje, že název domény nejvyšší úrovně se skládá z mezi dvěma a 24 znaky ASCII s alfanumerické znaky první a poslední a ostatní znaky, alfanumerické znaky nebo a pomlčku (-).</span><span class="sxs-lookup"><span data-stu-id="1d9b8-123">Instead, the regular expression merely verifies that the top-level domain name consists of between two and twenty-four ASCII characters, with alphanumeric first and last characters and the remaining characters being either alphanumeric or a hyphen (-).</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 <span data-ttu-id="1d9b8-124">V tomto příkladu regulární výraz ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`\` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-124">In this example, the regular expression pattern ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`\` is interpreted as shown in the following table.</span></span> <span data-ttu-id="1d9b8-125">Všimněte si, že regulární výraz zkompilován pomocí <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> příznak.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-125">Note that the regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>  
  
|<span data-ttu-id="1d9b8-126">Vzor</span><span class="sxs-lookup"><span data-stu-id="1d9b8-126">Pattern</span></span>|<span data-ttu-id="1d9b8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="1d9b8-127">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="1d9b8-128">Začne porovnávání na začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-128">Begin the match at the start of the string.</span></span>|  
|`(?(")`|<span data-ttu-id="1d9b8-129">Určete, zda je první znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-129">Determine whether the first character is a quotation mark.</span></span> <span data-ttu-id="1d9b8-130">`(?(")`je začátku alternace.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-130">`(?(")` is the beginning of an alternation construct.</span></span>|  
|`(?("")("".+?(?<!\\)""@)`|<span data-ttu-id="1d9b8-131">Je-li první znak je znak uvozovek, odpovídat začátku uvozovky následuje alespoň jeden výskyt libovolný znak, za nímž následuje koncové uvozovky.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-131">If the first character is a quotation mark, match a beginning quotation mark followed by at least one occurrence of any character, followed by an ending quotation mark.</span></span> <span data-ttu-id="1d9b8-132">Koncové uvozovky nesmí předcházet zpětné lomítko (\\).</span><span class="sxs-lookup"><span data-stu-id="1d9b8-132">The ending quotation mark must not be preceded by a backslash character (\\).</span></span> <span data-ttu-id="1d9b8-133">`(?<!`je začátku kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-133">`(?<!` is the beginning of a zero-width negative lookbehind assertion.</span></span> <span data-ttu-id="1d9b8-134">Řetězec by měl uzavřít s znaku zavináče (@).</span><span class="sxs-lookup"><span data-stu-id="1d9b8-134">The string should conclude with an at sign (@).</span></span>|  
|`&#124;(([0-9a-z]`|<span data-ttu-id="1d9b8-135">Je-li první znak není uvozovky, odpovídat libovolný znak abecedy z do z nebo A až Z (porovnání se malá a velká písmena), nebo jakékoli číselné znak od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-135">If the first character is not a quotation mark, match any alphabetic character from a to z or A to Z (the comparison is case insensitive), or any numeric character from 0 to 9.</span></span>|  
|`(\.(?!\.))`|<span data-ttu-id="1d9b8-136">Pokud další znak je dobou, shodovat se.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-136">If the next character is a period, match it.</span></span> <span data-ttu-id="1d9b8-137">Pokud není po dobu, Hledat na další znak a pokračovat na shodu.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-137">If it is not a period, look ahead to the next character and continue the match.</span></span> <span data-ttu-id="1d9b8-138">`(?!\.)`je negativního nulovou šířkou dopředného vyhledávání, která zabraňuje zobrazování v místní část e-mailovou adresu dvě po sobě jdoucí tečky.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-138">`(?!\.)` is a zero-width negative lookahead assertion that prevents two consecutive periods from appearing in the local part of an email address.</span></span>|  
|``&#124;[-!#\$%&'\*\+/=\?\^`{}\&#124;~\w]``|<span data-ttu-id="1d9b8-139">Pokud další znak není dobou, odpovídají libovolný znak nebo jeden z následujících znaků:-! #$%'*+=?^'{} &#124; ~.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-139">If the next character is not a period, match any word character or one of the following characters: -!#$%'*+=?^\`{}&#124;~.</span></span>|  
|``((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^`{}\&#124;~\w])*``|<span data-ttu-id="1d9b8-140">Shodují se vzorem alternace (období, za nímž následuje jiný období nebo jeden z a počet znaků) nula či více krát.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-140">Match the alternation pattern (a period followed by a non-period, or one of a number of characters) zero or more times.</span></span>|  
|`@`|<span data-ttu-id="1d9b8-141">Shoda znak @.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-141">Match the @ character.</span></span>|  
|`(?<=[0-9a-z])`|<span data-ttu-id="1d9b8-142">Pokračovat shody, pokud znak, který předchází @ – znak je A až Z, a až z nebo 0 až 9.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-142">Continue the match if the character that precedes the @ character is A through Z, a through z, or 0 through 9.</span></span> <span data-ttu-id="1d9b8-143">`(?<=[0-9a-z])` Konstrukce definuje výraz kladné zpětného vyhledávání s nulovou šířkou.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-143">The `(?<=[0-9a-z])` construct defines a zero-width positive lookbehind assertion.</span></span>|  
|`(?(\[)`|<span data-ttu-id="1d9b8-144">Zkontrolujte, zda je znak, který následuje @ levou hranatou závorku.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-144">Check whether the character that follows @ is an opening bracket.</span></span>|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|<span data-ttu-id="1d9b8-145">Pokud je levou hranatou závorku, odpovídat levá hranatá závorka následovaný IP adresu (čtyři sady číslic jednu až tři, každý sadou odděleny tečkou) a pravá závorka.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-145">If it is an opening bracket, match the opening bracket followed by an IP address (four sets of one to three digits, with each set separated by a period) and a closing bracket.</span></span>|  
|`&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`|<span data-ttu-id="1d9b8-146">Pokud je znak, který následuje @ není levou hranatou závorku, jeden alfanumerický znak shodu s hodnotou A-Z, a-z nebo 0-9, za nímž následuje nula nebo více výskytů pomlčka, za nímž následuje žádnou nebo jednu alfanumerický znak s hodnotou A-Z, a-z nebo 0-9 , za nímž následuje období.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-146">If the character that follows @ is not an opening bracket, match one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by zero or more occurrences of a hyphen, followed by zero or one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by a period.</span></span> <span data-ttu-id="1d9b8-147">Tento vzor lze opakovat, jeden či více krát a musí následovat název domény nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-147">This pattern can be repeated one or more times, and must be followed by the top-level domain name.</span></span>|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|<span data-ttu-id="1d9b8-148">Název domény nejvyšší úrovně musí začít a končit alfanumerickým znakem (a-z, A-Z a 0 – 9).</span><span class="sxs-lookup"><span data-stu-id="1d9b8-148">The top-level domain name must begin and end with an alphanumeric character (a-z, A-Z, and 0-9).</span></span> <span data-ttu-id="1d9b8-149">Může být také dostupný od nuly do 22 znaků ASCII, které jsou buď alfanumerické nebo pomlčky.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-149">It can also include from zero to 22 ASCII characters that are either alphanumeric or hyphens.</span></span>|  
|`$`|<span data-ttu-id="1d9b8-150">Ukončí porovnávání na konci řetězce.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-150">End the match at the end of the string.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1d9b8-151">Místo použití regulární výraz k ověření e-mailovou adresu, můžete použít <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-151">Instead of using a regular expression to validate an email address, you can use the <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="1d9b8-152">Pokud chcete zjistit, zda je platný e-mailovou adresu, předat e-mailovou adresu <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-152">To determine whether an email address is valid, pass the email address to the <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> class constructor.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d9b8-153">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1d9b8-153">Compiling the Code</span></span>  
 <span data-ttu-id="1d9b8-154">`IsValidEmail` a `DomainMapper` metody mohou být součástí knihovny metod nástroj regulární výraz nebo může být zahrnuta jako privátní statickou nebo instanci metody třídy aplikace.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-154">The `IsValidEmail` and `DomainMapper` methods can be included in a library of regular expression utility methods, or they can be included as private static or instance methods in the application class.</span></span>  
  
 <span data-ttu-id="1d9b8-155">Pro zahrnutí do knihovny regulárních výrazů, buď zkopírujte a vložte kód do projektu knihovny tříd Visual Studio, nebo zkopírujte a vložte ho do textového souboru a kompilaci z příkazového řádku pomocí příkazu takto (za předpokladu, že název zdrojového kódu  soubor je RegexUtilities.cs nebo RegexUtilities.vb:</span><span class="sxs-lookup"><span data-stu-id="1d9b8-155">To include them in a regular expression library, either copy and paste the code into a Visual Studio Class Library project, or copy and paste it into a text file and compile it from the command line with a command like the following (assuming that the name of the source code file is RegexUtilities.cs or RegexUtilities.vb:</span></span>  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 <span data-ttu-id="1d9b8-156">Můžete také <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> tak, aby zahrnoval regulárnímu výrazu v knihovně regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-156">You can also use the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> method to include this regular expression in a regular expression library.</span></span>  
  
 <span data-ttu-id="1d9b8-157">Pokud se používají v knihovně regulárního výrazu, můžete je volat pomocí kódu, například následující:</span><span class="sxs-lookup"><span data-stu-id="1d9b8-157">If they are used in a regular expression library, you can call them by using code such as the following:</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 <span data-ttu-id="1d9b8-158">Za předpokladu, že jste vytvořili knihovny tříd s názvem RegexUtilities.dll, která obsahuje vaše e-mailu ověření regulárního výrazu, můžete zkompilovat tento příklad v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="1d9b8-158">Assuming you've created a class library named RegexUtilities.dll that includes your email validation regular expression, you can compile this example in either of the following ways:</span></span>  
  
-   <span data-ttu-id="1d9b8-159">V sadě Visual Studio, vytvoření konzolové aplikace a přidáním odkaz na RegexUtilities.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="1d9b8-159">In Visual Studio, by creating a Console Application and adding a reference to RegexUtilities.dll to your project.</span></span>  
  
-   <span data-ttu-id="1d9b8-160">Z příkazového řádku, kopírování a vkládání zdrojový kód do textového souboru a kompilování pomocí příkazu takto (za předpokladu, že je název souboru se zdrojovým kódem Example.cs nebo Example.vb:</span><span class="sxs-lookup"><span data-stu-id="1d9b8-160">From the command line, by copying and pasting the source code into a text file and compiling it with a command like the following (assuming that the name of the source code file is Example.cs or Example.vb:</span></span>  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1d9b8-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d9b8-161">See Also</span></span>  
 [<span data-ttu-id="1d9b8-162">Regulární výrazy rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="1d9b8-162">.NET Framework Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
