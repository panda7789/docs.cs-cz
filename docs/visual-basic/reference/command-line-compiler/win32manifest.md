---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 901ea984a8e8e90329953a8936e68f2fc07f8847
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="b6c56-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6c56-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="b6c56-103">Identifikuje uživatelem definované souboru manifestu aplikace Win32, který má být vložen do souboru projektu přenosné spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="b6c56-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6c56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6c56-104">Syntax</span></span>  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6c56-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b6c56-105">Arguments</span></span>  
  
|<span data-ttu-id="b6c56-106">Termín</span><span class="sxs-lookup"><span data-stu-id="b6c56-106">Term</span></span>|<span data-ttu-id="b6c56-107">Definice</span><span class="sxs-lookup"><span data-stu-id="b6c56-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="b6c56-108">Cesta vlastního souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="b6c56-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6c56-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6c56-109">Remarks</span></span>  
 <span data-ttu-id="b6c56-110">Ve výchozím nastavení Visual Basic – kompilátor vloží manifest aplikace, která určuje požadovanou úroveň vykonávání asInvoker.</span><span class="sxs-lookup"><span data-stu-id="b6c56-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="b6c56-111">Manifest vytvoří ve stejné složce, ve kterém spustitelný soubor je vytvořen, obvykle bin\Debug nebo bin\Release složky při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b6c56-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="b6c56-112">Pokud chcete zadat vlastní manifest, např. Chcete-li určit požadovanou úroveň vykonávání highestAvailable nebo requireAdministrator, tuto možnost použijte k zadání názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="b6c56-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6c56-113">Tuto možnost a [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="b6c56-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="b6c56-114">Pokud se pokusíte použít obě možnosti ve stejném příkazovém řádku, zobrazí se chyba sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6c56-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="b6c56-115">Aplikace, která nemá žádné aplikace, manifest, který určuje že požadovanou úroveň vykonávání budou platit virtualizaci souborů a registrů pod funkci Řízení uživatelských účtů v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="b6c56-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="b6c56-116">Další informace o virtualizaci najdete v tématu [ClickOnce – nasazení v systému Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="b6c56-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="b6c56-117">Aplikace budou platit virtualizace, pokud platí některá z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="b6c56-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="b6c56-118">Můžete použít `-nowin32manifest` a neposkytuje manifest v pozdější fázi sestavování nebo jako součást souboru prostředků Windows (.res) pomocí `-win32resource` možnost.</span><span class="sxs-lookup"><span data-stu-id="b6c56-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2.  <span data-ttu-id="b6c56-119">Můžete zadat vlastní manifestu, který není uveden požadovanou úroveň vykonávání.</span><span class="sxs-lookup"><span data-stu-id="b6c56-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="b6c56-120">Visual Studio vytvoří výchozí soubor manifest a ukládá je v adresářích debug a release společně se spustitelným souborem.</span><span class="sxs-lookup"><span data-stu-id="b6c56-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="b6c56-121">Můžete zobrazit nebo upravit výchozí soubor app.manifest kliknutím **nastavení nástroje Řízení uživatelských účtů zobrazení** na **aplikace** kartě v Návrháři projektu.</span><span class="sxs-lookup"><span data-stu-id="b6c56-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="b6c56-122">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b6c56-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="b6c56-123">Manifest aplikace můžete poskytnout jako vlastní krok po sestavení nebo jako součást zdrojového souboru Win32 pomocí `-nowin32manifest` možnost.</span><span class="sxs-lookup"><span data-stu-id="b6c56-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="b6c56-124">Stejnou možnost použijte, pokud má vaše aplikace podléhat souborů nebo registru virtualizace v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="b6c56-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="b6c56-125">To zabrání kompilátoru z vytváření a vložení manifestu výchozí v souboru PE.</span><span class="sxs-lookup"><span data-stu-id="b6c56-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6c56-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6c56-126">Example</span></span>  
 <span data-ttu-id="b6c56-127">Následující příklad ukazuje výchozí manifest, Visual Basic – kompilátor vloží do PE.</span><span class="sxs-lookup"><span data-stu-id="b6c56-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6c56-128">Kompilátor vloží název standardní aplikace MyApplication.app do manifestu XML.</span><span class="sxs-lookup"><span data-stu-id="b6c56-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="b6c56-129">Toto je alternativní řešení Chcete-li povolit aplikací pro spuštění na Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="b6c56-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6c56-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6c56-130">See Also</span></span>  
 [<span data-ttu-id="b6c56-131">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b6c56-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b6c56-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6c56-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
