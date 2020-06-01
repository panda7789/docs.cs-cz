---
title: Jak získat informace o souborech, složkách a jednotkách – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 32aced17634a1406e2fce0af9c2a92f7a5eb9b40
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241614"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="b4cfb-102">Jak získat informace o souborech, složkách a jednotkách (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b4cfb-102">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>
<span data-ttu-id="b4cfb-103">V rozhraní .NET můžete získat přístup k informacím o systému souborů pomocí následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="b4cfb-103">In .NET, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="b4cfb-104"><xref:System.IO.FileInfo>Třídy a <xref:System.IO.DirectoryInfo> představují soubor nebo adresář, který obsahuje vlastnosti, které zveřejňují mnoho atributů souboru, které jsou podporovány systémem souborů NTFS.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="b4cfb-105">Obsahují také metody otevírání, zavírání, přesouvání a odstraňování souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="b4cfb-106">Instance těchto tříd lze vytvořit předáním řetězce, který představuje název souboru, složky nebo jednotky v konstruktoru do konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="b4cfb-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="b4cfb-107">Můžete také získat názvy souborů, složek nebo jednotek pomocí volání <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> , <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> a <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b4cfb-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b4cfb-108"><xref:System.IO.Directory?displayProperty=nameWithType>Třídy a <xref:System.IO.File?displayProperty=nameWithType> poskytují statické metody pro načítání informací o adresářích a souborech.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4cfb-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4cfb-109">Example</span></span>  
 <span data-ttu-id="b4cfb-110">Následující příklad ukazuje různé způsoby, jak získat přístup k informacím o souborech a složkách.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b4cfb-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b4cfb-111">Robust Programming</span></span>  
 <span data-ttu-id="b4cfb-112">Při zpracování řetězců cest zadaných uživatelem byste měli také zpracovat výjimky z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="b4cfb-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="b4cfb-113">Název souboru je poškozený.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-113">The file name is malformed.</span></span> <span data-ttu-id="b4cfb-114">Například obsahuje neplatné znaky nebo pouze mezery.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-114">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="b4cfb-115">Název souboru má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-115">The file name is null.</span></span>  
  
- <span data-ttu-id="b4cfb-116">Název souboru je delší než maximální délka definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-116">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="b4cfb-117">Název souboru obsahuje dvojtečku (:).</span><span class="sxs-lookup"><span data-stu-id="b4cfb-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="b4cfb-118">Pokud aplikace nemá dostatečná oprávnění ke čtení zadaného souboru, `Exists` vrátí metoda `false` bez ohledu na to, zda cesta existuje. metoda nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="b4cfb-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4cfb-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4cfb-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="b4cfb-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b4cfb-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b4cfb-121">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b4cfb-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
