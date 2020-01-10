---
title: Ověřování složitosti hesel
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 49e6f79c13c94a3f2f6891b259c4bb2bec54ae6f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344524"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="c4899-102">Návod: Ověření, že hesla jsou složitá (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c4899-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="c4899-103">Tato metoda kontroluje některé charakteristiky silného hesla a aktualizuje parametr řetězce o informace o tom, která Kontrola hesla se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="c4899-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="c4899-104">Hesla se dají použít v zabezpečeném systému k autorizaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="c4899-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="c4899-105">Nicméně hesla musí být obtížné pro odhad neautorizovaných uživatelů.</span><span class="sxs-lookup"><span data-stu-id="c4899-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="c4899-106">Útočníci můžou používat program pro *slovníkový útok* , který prochází všechna slova ve slovníku (nebo ve více slovnících v různých jazycích) a testuje, jestli některá slova fungují jako uživatelské heslo.</span><span class="sxs-lookup"><span data-stu-id="c4899-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="c4899-107">Slabá hesla, například "Yankees" nebo "Mustangu", se dají rychle uhodnout.</span><span class="sxs-lookup"><span data-stu-id="c4899-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="c4899-108">Silnější hesla, například "?L1N3vaFiNdMeyeP@sSWerd!, je mnohem méně pravděpodobný odhadnout.</span><span class="sxs-lookup"><span data-stu-id="c4899-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="c4899-109">Systém chráněný heslem by měl zajistit, aby si uživatelé zvolili silná hesla.</span><span class="sxs-lookup"><span data-stu-id="c4899-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="c4899-110">Silné heslo je složité (obsahující kombinaci velkých a malých písmen, číslic a speciálních znaků) a není to slovo.</span><span class="sxs-lookup"><span data-stu-id="c4899-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="c4899-111">Tento příklad ukazuje, jak ověřit složitost.</span><span class="sxs-lookup"><span data-stu-id="c4899-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4899-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4899-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="c4899-113">Kód</span><span class="sxs-lookup"><span data-stu-id="c4899-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="c4899-114">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c4899-114">Compile the code</span></span>  
 <span data-ttu-id="c4899-115">Zavolejte tuto metodu předáním řetězce, který obsahuje toto heslo.</span><span class="sxs-lookup"><span data-stu-id="c4899-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="c4899-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c4899-116">This example requires:</span></span>  
  
- <span data-ttu-id="c4899-117">Přístup k členům oboru názvů <xref:System.Text.RegularExpressions>.</span><span class="sxs-lookup"><span data-stu-id="c4899-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="c4899-118">Pokud plně nekvalifikujete názvy členů v kódu, přidejte `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c4899-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="c4899-119">Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c4899-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="c4899-120">Zabezpečení –</span><span class="sxs-lookup"><span data-stu-id="c4899-120">Security</span></span>  
 <span data-ttu-id="c4899-121">Pokud přesouváte heslo v síti, musíte pro přenos dat použít zabezpečenou metodu.</span><span class="sxs-lookup"><span data-stu-id="c4899-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="c4899-122">Další informace najdete v tématu [zabezpečení webových aplikací ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c4899-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="c4899-123">Přesnost funkce `ValidatePassword` můžete zlepšit přidáním dalších kontrol složitosti:</span><span class="sxs-lookup"><span data-stu-id="c4899-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="c4899-124">Porovnejte heslo a jeho podřetězce s uživatelským jménem, identifikátorem uživatele a slovníkem definovaným aplikací.</span><span class="sxs-lookup"><span data-stu-id="c4899-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="c4899-125">Kromě toho považovat vizuálně podobné znaky jako ekvivalentní při provádění porovnávání.</span><span class="sxs-lookup"><span data-stu-id="c4899-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="c4899-126">Například považovat písmena "l" a "e" za ekvivalent číslic "1" a "3".</span><span class="sxs-lookup"><span data-stu-id="c4899-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="c4899-127">Pokud je k dispozici pouze jeden znak velkými písmeny, ujistěte se, že se nejedná o první znak hesla.</span><span class="sxs-lookup"><span data-stu-id="c4899-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="c4899-128">Ujistěte se, že poslední dva znaky hesla jsou znaky písmen.</span><span class="sxs-lookup"><span data-stu-id="c4899-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="c4899-129">Nepovolujte hesla, ve kterých jsou všechny symboly zadány z horního řádku klávesnice.</span><span class="sxs-lookup"><span data-stu-id="c4899-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4899-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4899-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="c4899-131">[Zabezpečení webové aplikace ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c4899-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
