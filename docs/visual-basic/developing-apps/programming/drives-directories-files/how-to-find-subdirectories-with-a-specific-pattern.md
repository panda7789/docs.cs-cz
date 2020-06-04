---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 5b57914a518b568732955e5c73bb2031824c84dd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401625"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="07e2c-102">Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07e2c-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="07e2c-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>Metoda vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro podadresáře v adresáři.</span><span class="sxs-lookup"><span data-stu-id="07e2c-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="07e2c-104">`wildCards`K určení konkrétního vzoru můžete použít parametr.</span><span class="sxs-lookup"><span data-stu-id="07e2c-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="07e2c-105">Chcete-li do hledání zahrnout obsah podadresářů, nastavte `searchType` parametr na `SearchOption.SearchAllSubDirectories` .</span><span class="sxs-lookup"><span data-stu-id="07e2c-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="07e2c-106">Pokud se nenajde žádné adresáře vyhovující zadanému vzoru, vrátí se prázdná kolekce.</span><span class="sxs-lookup"><span data-stu-id="07e2c-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="07e2c-107">Vyhledání podadresářů s určitým vzorem</span><span class="sxs-lookup"><span data-stu-id="07e2c-107">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="07e2c-108">Použijte `GetDirectories` metodu, zadejte název a cestu adresáře, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="07e2c-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="07e2c-109">Následující příklad vrátí všechny adresáře ve struktuře adresáře, které obsahují slovo "logs" v názvu a přidá je do `ListBox1` .</span><span class="sxs-lookup"><span data-stu-id="07e2c-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="07e2c-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="07e2c-110">Robust Programming</span></span>

<span data-ttu-id="07e2c-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="07e2c-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="07e2c-112">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="07e2c-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="07e2c-113">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="07e2c-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="07e2c-114">Jeden nebo více zadaných zástupných znaků je `Nothing` , prázdný řetězec nebo obsahuje pouze mezery ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="07e2c-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="07e2c-115">`directory`neexistuje ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="07e2c-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="07e2c-116">`directory`odkazuje na existující soubor ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="07e2c-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="07e2c-117">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="07e2c-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="07e2c-118">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="07e2c-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="07e2c-119">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="07e2c-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="07e2c-120">Uživatel nemá potřebná oprávnění ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="07e2c-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="07e2c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="07e2c-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="07e2c-122">Postupy: Hledání souborů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="07e2c-122">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
