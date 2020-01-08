---
title: Jak získat informace o souborech, složkách a jednotkách – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: e8bd65b1c8c24f69d280cf69deaf25daf7cf8818
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635389"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="70c03-102">Jak získat informace o souborech, složkách a jednotkách (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="70c03-102">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>
<span data-ttu-id="70c03-103">V .NET Framework můžete získat přístup k informacím o systému souborů pomocí následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="70c03-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="70c03-104">Třídy <xref:System.IO.FileInfo> a <xref:System.IO.DirectoryInfo> představují soubor nebo adresář a obsahují vlastnosti, které zveřejňují mnoho atributů souboru, které jsou podporovány systémem souborů NTFS.</span><span class="sxs-lookup"><span data-stu-id="70c03-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="70c03-105">Obsahují také metody otevírání, zavírání, přesouvání a odstraňování souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="70c03-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="70c03-106">Instance těchto tříd lze vytvořit předáním řetězce, který představuje název souboru, složky nebo jednotky v konstruktoru do konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="70c03-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="70c03-107">Můžete také získat názvy souborů, složek nebo jednotek pomocí volání <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>a <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70c03-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="70c03-108">Třídy <xref:System.IO.Directory?displayProperty=nameWithType> a <xref:System.IO.File?displayProperty=nameWithType> poskytují statické metody pro načítání informací o adresářích a souborech.</span><span class="sxs-lookup"><span data-stu-id="70c03-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70c03-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="70c03-109">Example</span></span>  
 <span data-ttu-id="70c03-110">Následující příklad ukazuje různé způsoby, jak získat přístup k informacím o souborech a složkách.</span><span class="sxs-lookup"><span data-stu-id="70c03-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="70c03-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="70c03-111">Robust Programming</span></span>  
 <span data-ttu-id="70c03-112">Při zpracování řetězců cest zadaných uživatelem byste měli také zpracovat výjimky z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="70c03-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="70c03-113">Název souboru je poškozený.</span><span class="sxs-lookup"><span data-stu-id="70c03-113">The file name is malformed.</span></span> <span data-ttu-id="70c03-114">Například obsahuje neplatné znaky nebo pouze mezery.</span><span class="sxs-lookup"><span data-stu-id="70c03-114">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="70c03-115">Název souboru má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="70c03-115">The file name is null.</span></span>  
  
- <span data-ttu-id="70c03-116">Název souboru je delší než maximální délka definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="70c03-116">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="70c03-117">Název souboru obsahuje dvojtečku (:).</span><span class="sxs-lookup"><span data-stu-id="70c03-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="70c03-118">Pokud aplikace nemá dostatečná oprávnění ke čtení zadaného souboru, metoda `Exists` vrátí `false` bez ohledu na to, zda cesta existuje. metoda nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="70c03-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c03-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70c03-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="70c03-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="70c03-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="70c03-121">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="70c03-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
