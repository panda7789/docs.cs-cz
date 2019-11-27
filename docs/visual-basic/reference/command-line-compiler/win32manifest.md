---
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: cef1e6c19e7fdd6fc9f42c8fc36008314ea80a80
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349135"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="79f3d-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79f3d-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="79f3d-103">Identifikuje uživatelsky definovaný soubor manifestu aplikace Win32, který bude vložen do přenositelného spustitelného souboru (PE) projektu.</span><span class="sxs-lookup"><span data-stu-id="79f3d-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79f3d-104">Syntax</span></span>  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="79f3d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="79f3d-105">Arguments</span></span>  
  
|<span data-ttu-id="79f3d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="79f3d-106">Term</span></span>|<span data-ttu-id="79f3d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="79f3d-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="79f3d-108">Cesta k souboru vlastního manifestu.</span><span class="sxs-lookup"><span data-stu-id="79f3d-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79f3d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79f3d-109">Remarks</span></span>  
 <span data-ttu-id="79f3d-110">Ve výchozím nastavení vloží kompilátor Visual Basic manifest aplikace, který určuje požadovanou úroveň spuštění podle volajícího.</span><span class="sxs-lookup"><span data-stu-id="79f3d-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="79f3d-111">Vytvoří manifest ve stejné složce, ve které je sestaven spustitelný soubor, obvykle složka bin\Debug nebo bin\Release při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79f3d-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="79f3d-112">Pokud chcete zadat vlastní manifest, například pro určení požadované úrovně spuštění nejvyšší dostupná nebo vyžadovat správce, použijte tuto možnost k zadání názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="79f3d-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79f3d-113">Tato možnost a možnost [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="79f3d-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="79f3d-114">Pokud se pokusíte použít obě možnosti na stejném příkazovém řádku, zobrazí se chyba buildu.</span><span class="sxs-lookup"><span data-stu-id="79f3d-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="79f3d-115">Aplikace, která nemá žádný manifest aplikace, který určuje požadovanou úroveň spuštění, bude podléhat virtualizaci souborů nebo registru v rámci funkce řízení uživatelských účtů v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="79f3d-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="79f3d-116">Další informace o virtualizaci najdete v tématu [nasazení ClickOnce v systému Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="79f3d-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="79f3d-117">Pokud je splněna některá z následujících podmínek, bude se aplikace vztahovat k virtualizaci:</span><span class="sxs-lookup"><span data-stu-id="79f3d-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1. <span data-ttu-id="79f3d-118">Použijete možnost `-nowin32manifest` a neposkytnete manifest v pozdějším kroku sestavení nebo jako součást souboru prostředků Windows (. res) pomocí možnosti `-win32resource`.</span><span class="sxs-lookup"><span data-stu-id="79f3d-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2. <span data-ttu-id="79f3d-119">Poskytnete vlastní manifest, který neurčuje požadovanou úroveň spuštění.</span><span class="sxs-lookup"><span data-stu-id="79f3d-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="79f3d-120">Visual Studio vytvoří soubor default. manifest a uloží ho do adresářů pro ladění a vydání spolu se spustitelným souborem.</span><span class="sxs-lookup"><span data-stu-id="79f3d-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="79f3d-121">Výchozí soubor App. manifest můžete zobrazit nebo upravit kliknutím na **Zobrazit nastavení nástroje řízení uživatelských účtů** na kartě **aplikace** v Návrháři projektu.</span><span class="sxs-lookup"><span data-stu-id="79f3d-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="79f3d-122">Další informace naleznete na [stránce aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="79f3d-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="79f3d-123">Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást souboru prostředků Win32 pomocí možnosti `-nowin32manifest`.</span><span class="sxs-lookup"><span data-stu-id="79f3d-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="79f3d-124">Tuto možnost použijte, pokud chcete, aby se vaše aplikace mohla vztahovat k virtualizaci souborů nebo registru v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="79f3d-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="79f3d-125">Tím zabráníte kompilátoru v vytvoření a vložení výchozího manifestu do souboru PE.</span><span class="sxs-lookup"><span data-stu-id="79f3d-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79f3d-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="79f3d-126">Example</span></span>  
 <span data-ttu-id="79f3d-127">Následující příklad ukazuje výchozí manifest, který Visual Basic Kompilátor vloží do PE.</span><span class="sxs-lookup"><span data-stu-id="79f3d-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79f3d-128">Kompilátor vloží do souboru XML manifestu standardní název aplikace MyApplication. app.</span><span class="sxs-lookup"><span data-stu-id="79f3d-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="79f3d-129">Toto je alternativní řešení pro povolení spouštění aplikací v systému Windows Server 2003 s aktualizací Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="79f3d-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79f3d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79f3d-130">See also</span></span>

- [<span data-ttu-id="79f3d-131">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="79f3d-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="79f3d-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79f3d-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
