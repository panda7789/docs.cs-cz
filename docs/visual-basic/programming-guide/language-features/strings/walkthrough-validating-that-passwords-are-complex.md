---
title: Ověřování složitosti hesla (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 829d6485acdca22fbf10160c734e5c7f931dd855
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824933"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="64a55-102">Návod: Ověření, že hesla jsou složitá (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64a55-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="64a55-103">Tato metoda zkontroluje některé vlastnosti silné heslo a aktualizuje řetězcový parametr s informacemi o tom, které kontroluje heslo selže.</span><span class="sxs-lookup"><span data-stu-id="64a55-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="64a55-104">Hesla je možné v zabezpečeném systému k autorizaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="64a55-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="64a55-105">Hesla musí být ale obtížné pro neoprávněné uživatele o.</span><span class="sxs-lookup"><span data-stu-id="64a55-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="64a55-106">Útočníci můžou používat *slovníkový útok* programu, který prochází všechna slova ve slovníku (nebo více adresářů v různých jazycích) a testuje, jestli některý z slov fungovat jako heslo uživatele.</span><span class="sxs-lookup"><span data-stu-id="64a55-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="64a55-107">Slabá hesla, jako je například "Yankees" nebo "Mustang" dají uhodnout rychle.</span><span class="sxs-lookup"><span data-stu-id="64a55-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="64a55-108">Volba bezpečnějších hesel, jako například "? Je "L1N3vaFiNdMeyeP@sSWerd!", jsou mnohem méně pravděpodobné, že dají uhodnout.</span><span class="sxs-lookup"><span data-stu-id="64a55-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="64a55-109">Systém chráněný heslem se ujistěte, že uživatelé vybrat silná hesla.</span><span class="sxs-lookup"><span data-stu-id="64a55-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="64a55-110">Silné heslo je složitý (obsahují kombinaci velká písmena, malá písmena, číselné a speciální znaky) a není u slov velká.</span><span class="sxs-lookup"><span data-stu-id="64a55-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="64a55-111">Tento příklad ukazuje, jak ověřit složitost.</span><span class="sxs-lookup"><span data-stu-id="64a55-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64a55-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="64a55-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="64a55-113">Kód</span><span class="sxs-lookup"><span data-stu-id="64a55-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="64a55-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="64a55-114">Compiling the Code</span></span>  
 <span data-ttu-id="64a55-115">Tuto metodu volejte předáním řetězce, který obsahuje toto heslo.</span><span class="sxs-lookup"><span data-stu-id="64a55-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="64a55-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="64a55-116">This example requires:</span></span>  
  
-   <span data-ttu-id="64a55-117">Přístup k členům <xref:System.Text.RegularExpressions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="64a55-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="64a55-118">Přidat `Imports` příkazu, pokud jste nejsou kvalifikaci plně názvy členů ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="64a55-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="64a55-119">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="64a55-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="64a55-120">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="64a55-120">Security</span></span>  
 <span data-ttu-id="64a55-121">Pokud přesouváte hesla přes síť, budete muset použít bezpečnou metodu pro přenášení dat.</span><span class="sxs-lookup"><span data-stu-id="64a55-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="64a55-122">Další informace najdete v tématu [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="64a55-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="64a55-123">Můžete zvýšit jeho přesnost `ValidatePassword` funkce tak, že přidáte další složitosti kontroly:</span><span class="sxs-lookup"><span data-stu-id="64a55-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="64a55-124">Porovnejte heslo a jeho dílčí řetězce na jméno uživatele, identifikátor uživatele a slovníku definovaného aplikací.</span><span class="sxs-lookup"><span data-stu-id="64a55-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="64a55-125">Kromě toho považovat za vizuálně podobné znaky ekvivalent při provádění porovnání.</span><span class="sxs-lookup"><span data-stu-id="64a55-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="64a55-126">Například považovat za písmena "l" a "e" odpovídá číslice "1" a "3".</span><span class="sxs-lookup"><span data-stu-id="64a55-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="64a55-127">Pokud existuje pouze jedno velké písmeno, ujistěte se, že se nejedná o první znak hesla.</span><span class="sxs-lookup"><span data-stu-id="64a55-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="64a55-128">Ujistěte se, že poslední dva znaky heslo jsou znaky písmena.</span><span class="sxs-lookup"><span data-stu-id="64a55-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="64a55-129">Nepovolit hesla, ve které jsou zadány všechny symboly z horní řádek klávesnici.</span><span class="sxs-lookup"><span data-stu-id="64a55-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a55-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64a55-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="64a55-131">[Zabezpečení webové aplikace ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64a55-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
