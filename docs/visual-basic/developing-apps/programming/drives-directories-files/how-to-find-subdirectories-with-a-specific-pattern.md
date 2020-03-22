---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348771"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="33ccb-102">Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="33ccb-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="33ccb-103">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> vrátí kolekci řetězců jen pro čtení představující názvy cest pro podadresáře v adresáři.</span><span class="sxs-lookup"><span data-stu-id="33ccb-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="33ccb-104">`wildCards` Parametr můžete použít k určení určitého vzoru.</span><span class="sxs-lookup"><span data-stu-id="33ccb-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="33ccb-105">Pokud chcete do hledání zahrnout obsah podadresářů, nastavte `searchType` parametr `SearchOption.SearchAllSubDirectories`na .</span><span class="sxs-lookup"><span data-stu-id="33ccb-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="33ccb-106">Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné adresáře odpovídající zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="33ccb-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="33ccb-107">Vyhledání podadresářů s určitým vzorem</span><span class="sxs-lookup"><span data-stu-id="33ccb-107">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="33ccb-108">Použijte `GetDirectories` metodu, která poskytuje název a cestu adresáře, který chcete prohledat.</span><span class="sxs-lookup"><span data-stu-id="33ccb-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="33ccb-109">Následující příklad vrátí všechny adresáře ve struktuře adresářů, které obsahují slovo "Protokoly" v jejich názvu a přidá je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="33ccb-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="33ccb-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="33ccb-110">Robust Programming</span></span>

<span data-ttu-id="33ccb-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="33ccb-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="33ccb-112">Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="33ccb-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="33ccb-113">Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).</span><span class="sxs-lookup"><span data-stu-id="33ccb-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="33ccb-114">Jeden nebo více zadaných zástupných znaků je `Nothing`prázdný řetězec<xref:System.ArgumentNullException>nebo obsahuje pouze mezery ( ).</span><span class="sxs-lookup"><span data-stu-id="33ccb-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="33ccb-115">`directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="33ccb-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="33ccb-116">`directory`odkazuje na existující<xref:System.IO.IOException>soubor ( ).</span><span class="sxs-lookup"><span data-stu-id="33ccb-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="33ccb-117">Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).</span><span class="sxs-lookup"><span data-stu-id="33ccb-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="33ccb-118">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="33ccb-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="33ccb-119">Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).</span><span class="sxs-lookup"><span data-stu-id="33ccb-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="33ccb-120">Uživatel nemá potřebná<xref:System.UnauthorizedAccessException>oprávnění ( ).</span><span class="sxs-lookup"><span data-stu-id="33ccb-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="33ccb-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="33ccb-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="33ccb-122">Postupy: Hledání souborů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="33ccb-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
