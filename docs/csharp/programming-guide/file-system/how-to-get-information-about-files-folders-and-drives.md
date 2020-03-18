---
title: Jak získat informace o souborech, složkách a jednotkách – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 6024b1be4ce826900c6f9b367323fb19ac55d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705207"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="93038-102">Jak získat informace o souborech, složkách a jednotkách (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="93038-102">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>
<span data-ttu-id="93038-103">V rozhraní .NET Framework můžete získat přístup k informacím o systému souborů pomocí následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="93038-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="93038-104"><xref:System.IO.FileInfo> Třídy <xref:System.IO.DirectoryInfo> a představují soubor nebo adresář a obsahují vlastnosti, které zveřejňují mnoho atributů souborů podporovaných systémem souborů NTFS.</span><span class="sxs-lookup"><span data-stu-id="93038-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="93038-105">Obsahují také metody pro otevírání, zavírání, přesouvání a odstraňování souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="93038-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="93038-106">Instance těchto tříd můžete vytvořit předáním řetězce, který představuje název souboru, složky nebo jednotky do konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="93038-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="93038-107">Názvy souborů, složek nebo jednotek můžete získat <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>také <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>pomocí volání aplikace , a .</span><span class="sxs-lookup"><span data-stu-id="93038-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="93038-108"><xref:System.IO.Directory?displayProperty=nameWithType> Třídy <xref:System.IO.File?displayProperty=nameWithType> a poskytují statické metody pro načítání informací o adresářích a souborech.</span><span class="sxs-lookup"><span data-stu-id="93038-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93038-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="93038-109">Example</span></span>  
 <span data-ttu-id="93038-110">Následující příklad ukazuje různé způsoby přístupu k informacím o souborech a složkách.</span><span class="sxs-lookup"><span data-stu-id="93038-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="93038-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="93038-111">Robust Programming</span></span>  
 <span data-ttu-id="93038-112">Při zpracování řetězců cesty zadané uživatelem byste měli také zpracovávat výjimky pro následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="93038-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="93038-113">Název souboru je poškozen.</span><span class="sxs-lookup"><span data-stu-id="93038-113">The file name is malformed.</span></span> <span data-ttu-id="93038-114">Obsahuje například neplatné znaky nebo pouze prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="93038-114">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="93038-115">Název souboru je null.</span><span class="sxs-lookup"><span data-stu-id="93038-115">The file name is null.</span></span>  
  
- <span data-ttu-id="93038-116">Název souboru je delší než maximální délka definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="93038-116">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="93038-117">Název souboru obsahuje dvojtečku (:).</span><span class="sxs-lookup"><span data-stu-id="93038-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="93038-118">Pokud aplikace nemá dostatečná oprávnění ke čtení `Exists` zadaného `false` souboru, metoda vrátí bez ohledu na to, zda existuje cesta; metoda nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="93038-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93038-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="93038-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="93038-120">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="93038-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="93038-121">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="93038-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
