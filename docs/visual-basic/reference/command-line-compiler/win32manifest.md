---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: bd9a708b99d11b90e47c3413bb0003ce2def13a1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833712"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="c540f-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c540f-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="c540f-103">Určuje uživatelský soubor manifestu aplikace Win32, který má být vložen do projektu soubor (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="c540f-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c540f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c540f-104">Syntax</span></span>  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="c540f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c540f-105">Arguments</span></span>  
  
|<span data-ttu-id="c540f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="c540f-106">Term</span></span>|<span data-ttu-id="c540f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c540f-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="c540f-108">Cesta vlastního souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="c540f-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c540f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c540f-109">Remarks</span></span>  
 <span data-ttu-id="c540f-110">Ve výchozím nastavení vloží kompilátor jazyka Visual Basic, která určuje požadovanou úroveň spuštění asInvoker manifestu aplikace.</span><span class="sxs-lookup"><span data-stu-id="c540f-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="c540f-111">Manifest vytvoří ve stejné složce, ve kterém spustitelného souboru, který je sestaven, obvykle bin\Debug nebo bin\Release složky, pokud používáte sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c540f-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="c540f-112">Pokud chcete zadat vlastní manifest, třeba když chcete požadovanou úroveň spuštění highestAvailable nebo requireAdministrator, zadejte tuto možnost použijte k zadání názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="c540f-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c540f-113">Tuto možnost a [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) možnost se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="c540f-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="c540f-114">Pokud se pokusíte použít obě možnosti jsou ve stejném příkazovém řádku, zobrazí se chyba buildu.</span><span class="sxs-lookup"><span data-stu-id="c540f-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="c540f-115">Aplikace nemá žádné aplikace, manifest, který určuje, že že požadovanou úroveň spuštění bude v souladu s virtualizací souborů nebo registru pod funkci Řízení uživatelských účtů ve Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c540f-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="c540f-116">Další informace o virtualizaci, naleznete v tématu [nasazení ClickOnce v systému Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="c540f-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="c540f-117">Vaše aplikace bude v souladu s virtualizace, pokud je splněna jedna z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="c540f-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="c540f-118">Můžete použít `-nowin32manifest` a neposkytuje manifest v pozdějším kroku sestavení nebo jako součást souboru prostředků (.res) Windows s použitím `-win32resource` možnost.</span><span class="sxs-lookup"><span data-stu-id="c540f-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2.  <span data-ttu-id="c540f-119">Poskytnete vlastního manifestu, která neurčuje požadovanou úroveň spuštění.</span><span class="sxs-lookup"><span data-stu-id="c540f-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="c540f-120">Visual Studio vytvoří výchozí soubor .manifest a ukládá ho do adresáře debug a release spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c540f-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="c540f-121">Můžete zobrazit nebo upravit výchozí soubor app.manifest kliknutím **nastavení nástroje Řízení uživatelských účtů zobrazení** na **aplikace** kartě v Návrháři projektu.</span><span class="sxs-lookup"><span data-stu-id="c540f-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="c540f-122">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c540f-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="c540f-123">Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást soubor prostředků Win32 pomocí `-nowin32manifest` možnost.</span><span class="sxs-lookup"><span data-stu-id="c540f-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="c540f-124">Stejnou možnost použijte, pokud chcete, aby byla v souladu s virtualizací souborů nebo registru v systému Windows Vista aplikace.</span><span class="sxs-lookup"><span data-stu-id="c540f-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="c540f-125">To zabrání kompilátoru od vytvoření a vložení výchozí manifest do souboru PE.</span><span class="sxs-lookup"><span data-stu-id="c540f-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c540f-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="c540f-126">Example</span></span>  
 <span data-ttu-id="c540f-127">Následující příklad ukazuje výchozí manifest, že kompilátor jazyka Visual Basic vloží do PE.</span><span class="sxs-lookup"><span data-stu-id="c540f-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c540f-128">Kompilátor vloží název standardní aplikace MyApplication.app do manifestu XML.</span><span class="sxs-lookup"><span data-stu-id="c540f-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="c540f-129">Toto je alternativní řešení Chcete-li povolit aplikace, které poběží na Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="c540f-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c540f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c540f-130">See also</span></span>

- [<span data-ttu-id="c540f-131">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="c540f-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c540f-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c540f-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
