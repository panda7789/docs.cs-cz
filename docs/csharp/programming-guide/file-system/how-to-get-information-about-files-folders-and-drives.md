---
title: "Postupy: Získávání informací o souborech, složkách a jednotkách (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5652dda53a0192ce39be497b6e8ad3c97bef042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="30188-102">Postupy: Získávání informací o souborech, složkách a jednotkách (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="30188-102">How to: Get Information About Files, Folders, and Drives  (C# Programming Guide)</span></span>
<span data-ttu-id="30188-103">V rozhraní .NET Framework můžete přístup k informacím systému souboru pomocí následující třídy:</span><span class="sxs-lookup"><span data-stu-id="30188-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="30188-104"><xref:System.IO.FileInfo> a <xref:System.IO.DirectoryInfo> třídy představují soubor nebo adresář a obsahovat vlastnosti, které zveřejňují mnoho atributů souborů, které jsou podporovány v systému souborů NTFS.</span><span class="sxs-lookup"><span data-stu-id="30188-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="30188-105">Také obsahují metody pro otevření, zavření, přesun a odstraňování souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="30188-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="30188-106">Instance těchto tříd lze vytvořit pomocí předání řetězec, který představuje název souboru, složce nebo jednotce v konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="30188-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="30188-107">Názvy souborů, složek nebo jednotky můžete také získat pomocí volání <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, a <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30188-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="30188-108"><xref:System.IO.Directory?displayProperty=nameWithType> a <xref:System.IO.File?displayProperty=nameWithType> tříd poskytuje statické metody pro načtení informací o adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="30188-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30188-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="30188-109">Example</span></span>  
 <span data-ttu-id="30188-110">Následující příklad ukazuje různé způsoby přístup k informacím o soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="30188-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="30188-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="30188-111">Robust Programming</span></span>  
 <span data-ttu-id="30188-112">Když při zpracování řetězce cesty zadané uživatelem, by také zpracování výjimky pro tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="30188-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
-   <span data-ttu-id="30188-113">Název souboru je poškozený.</span><span class="sxs-lookup"><span data-stu-id="30188-113">The file name is malformed.</span></span> <span data-ttu-id="30188-114">Například obsahuje neplatné znaky nebo jenom prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="30188-114">For example, it contains invalid characters or only white space.</span></span>  
  
-   <span data-ttu-id="30188-115">Název souboru má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="30188-115">The file name is null.</span></span>  
  
-   <span data-ttu-id="30188-116">Název souboru je delší než maximální délka definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="30188-116">The file name is longer than the system-defined maximum length.</span></span>  
  
-   <span data-ttu-id="30188-117">Název souboru obsahuje dvojtečku (:).</span><span class="sxs-lookup"><span data-stu-id="30188-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="30188-118">Pokud aplikace nemá dostatečná oprávnění ke čtení zadaného souboru, `Exists` metoda vrátí `false` bez ohledu na tom, zda cesta existuje; metoda nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="30188-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30188-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="30188-119">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="30188-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="30188-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="30188-121">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="30188-121">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
