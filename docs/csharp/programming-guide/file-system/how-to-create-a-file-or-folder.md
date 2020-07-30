---
title: Postup vytvoření souboru nebo složky – Průvodce programováním v C#
description: Naučte se vytvářet soubory nebo složky programově. Můžete vytvořit složku, podsložku, soubor v podsložce a zapsat data do tohoto souboru.
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: f5641dc765b1a2d62adb76babe3f111730d4550b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302682"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="69395-104">Postup vytvoření souboru nebo složky (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="69395-104">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="69395-105">Můžete programově vytvořit složku v počítači, vytvořit podsložku, vytvořit soubor v podsložce a zapsat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="69395-105">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69395-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="69395-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="69395-107">Pokud složka již existuje, <xref:System.IO.Directory.CreateDirectory%2A> neprovede žádnou akci a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="69395-107">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="69395-108">Ale <xref:System.IO.File.Create%2A?displayProperty=nameWithType> nahradí existující soubor novým souborem.</span><span class="sxs-lookup"><span data-stu-id="69395-108">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="69395-109">V příkladu se používá `if` - `else` příkaz, který brání v nahrazení existujícího souboru.</span><span class="sxs-lookup"><span data-stu-id="69395-109">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="69395-110">Provedením následujících změn v příkladu můžete určit různé výsledky na základě toho, zda soubor s určitým názvem již existuje.</span><span class="sxs-lookup"><span data-stu-id="69395-110">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="69395-111">Pokud takový soubor neexistuje, kód ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="69395-111">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="69395-112">Pokud takový soubor existuje, kód připojí data do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="69395-112">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="69395-113">Zadejte jiný než náhodný název souboru.</span><span class="sxs-lookup"><span data-stu-id="69395-113">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="69395-114">Nahraďte `if` - `else` příkaz `using` příkazem v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="69395-114">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="69395-115">Spusťte příklad několikrát, abyste ověřili, že se data do souboru přidávají pokaždé.</span><span class="sxs-lookup"><span data-stu-id="69395-115">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="69395-116">Další `FileMode` hodnoty, které můžete vyzkoušet, najdete v tématu <xref:System.IO.FileMode> .</span><span class="sxs-lookup"><span data-stu-id="69395-116">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="69395-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="69395-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="69395-118">Název složky je poškozený.</span><span class="sxs-lookup"><span data-stu-id="69395-118">The folder name is malformed.</span></span> <span data-ttu-id="69395-119">Například obsahuje neplatné znaky nebo je pouze mezera ( <xref:System.ArgumentException> třída).</span><span class="sxs-lookup"><span data-stu-id="69395-119">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="69395-120">Použijte <xref:System.IO.Path> třídu k vytvoření platných názvů cest.</span><span class="sxs-lookup"><span data-stu-id="69395-120">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="69395-121">Nadřazená složka složky, která se má vytvořit, je jen pro čtení ( <xref:System.IO.IOException> třída).</span><span class="sxs-lookup"><span data-stu-id="69395-121">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="69395-122">Název složky je `null` ( <xref:System.ArgumentNullException> Class).</span><span class="sxs-lookup"><span data-stu-id="69395-122">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="69395-123">Název složky je příliš dlouhý ( <xref:System.IO.PathTooLongException> třída).</span><span class="sxs-lookup"><span data-stu-id="69395-123">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="69395-124">Název složky je pouze dvojtečka, ":" ( <xref:System.IO.PathTooLongException> třída).</span><span class="sxs-lookup"><span data-stu-id="69395-124">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="69395-125">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="69395-125">.NET Security</span></span>  
 <span data-ttu-id="69395-126">Instance <xref:System.Security.SecurityException> třídy může být vyvolána v situacích částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="69395-126">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="69395-127">Pokud nemáte oprávnění k vytvoření složky, příklad vyvolá instanci <xref:System.UnauthorizedAccessException> třídy.</span><span class="sxs-lookup"><span data-stu-id="69395-127">If you don't have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69395-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69395-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="69395-129">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="69395-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="69395-130">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="69395-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
