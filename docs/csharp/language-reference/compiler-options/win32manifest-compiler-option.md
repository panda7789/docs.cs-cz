---
description: -win32manifest (možnosti kompilátoru C#)
title: -win32manifest (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 4ce4033323eb938caff1d769198ca69782b470ab
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140825"
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="9cb55-103">-win32manifest (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="9cb55-103">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="9cb55-104">Pomocí možnosti **-win32manifest** určete uživatelsky definovaný soubor manifestu aplikace Win32, který bude vložen do přenositelného spustitelného souboru (PE) projektu.</span><span class="sxs-lookup"><span data-stu-id="9cb55-104">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb55-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cb55-105">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9cb55-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9cb55-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9cb55-107">Název a umístění vlastního souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="9cb55-107">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cb55-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cb55-108">Remarks</span></span>  
 <span data-ttu-id="9cb55-109">Ve výchozím nastavení kompilátor Visual C# vloží manifest aplikace, který určuje požadovanou úroveň spuštění "podle volajícího".</span><span class="sxs-lookup"><span data-stu-id="9cb55-109">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="9cb55-110">Vytvoří manifest ve stejné složce, ve které je sestaven spustitelný soubor, obvykle složka bin\Debug nebo bin\Release při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9cb55-110">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="9cb55-111">Pokud chcete zadat vlastní manifest, například pro určení požadované úrovně spuštění "nejvyšší dostupná" nebo "vyžadovat správce", použijte tuto možnost k zadání názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="9cb55-111">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9cb55-112">Tato možnost a možnost [-win32res (možnosti kompilátoru C#)](./win32res-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="9cb55-112">This option and the [-win32res (C# Compiler Options)](./win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="9cb55-113">Pokud se pokusíte použít obě možnosti na stejném příkazovém řádku, zobrazí se chyba buildu.</span><span class="sxs-lookup"><span data-stu-id="9cb55-113">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="9cb55-114">Aplikace, která nemá žádný manifest aplikace, který určuje požadovanou úroveň spuštění, bude v rámci funkce řízení uživatelských účtů ve Windows podléhat virtualizaci File/Registry.</span><span class="sxs-lookup"><span data-stu-id="9cb55-114">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="9cb55-115">Další informace najdete v tématu [řízení uživatelských účtů](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="9cb55-115">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="9cb55-116">Vaše aplikace bude platit z virtualizace, pokud je splněna jedna z těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="9cb55-116">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
- <span data-ttu-id="9cb55-117">Použijete možnost **-nowin32manifest** a neposkytnete manifest v pozdějším kroku sestavení nebo jako součást souboru prostředků Windows (. res) pomocí možnosti **-win32res** .</span><span class="sxs-lookup"><span data-stu-id="9cb55-117">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
- <span data-ttu-id="9cb55-118">Poskytnete vlastní manifest, který neurčuje požadovanou úroveň spuštění.</span><span class="sxs-lookup"><span data-stu-id="9cb55-118">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="9cb55-119">Visual Studio vytvoří soubor default. manifest a uloží ho do adresářů pro ladění a vydání spolu se spustitelným souborem.</span><span class="sxs-lookup"><span data-stu-id="9cb55-119">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="9cb55-120">Vlastní manifest můžete přidat tak, že ho vytvoříte v libovolném textovém editoru a pak ho přidáte do projektu.</span><span class="sxs-lookup"><span data-stu-id="9cb55-120">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="9cb55-121">Případně můžete kliknout pravým tlačítkem myši na ikonu **projektu** v **Průzkumník řešení**, kliknout na **Přidat novou položku**a pak kliknout na **soubor manifestu aplikace**.</span><span class="sxs-lookup"><span data-stu-id="9cb55-121">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="9cb55-122">Po přidání nového nebo existujícího souboru manifestu se zobrazí v rozevíracím seznamu **manifest** .</span><span class="sxs-lookup"><span data-stu-id="9cb55-122">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="9cb55-123">Další informace naleznete na [stránce aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="9cb55-123">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="9cb55-124">Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást souboru prostředků Win32 pomocí možnosti [-nowin32manifest (možnosti kompilátoru C#)](./nowin32manifest-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="9cb55-124">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](./nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="9cb55-125">Tuto možnost použijte, pokud chcete, aby se vaše aplikace mohla vztahovat k virtualizaci souborů nebo registru v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="9cb55-125">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="9cb55-126">Tím zabráníte kompilátoru v vytváření a vkládání výchozího manifestu do přenositelného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="9cb55-126">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cb55-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cb55-127">Example</span></span>  
 <span data-ttu-id="9cb55-128">Následující příklad ukazuje výchozí manifest, který kompilátor jazyka Visual C# vloží do PE.</span><span class="sxs-lookup"><span data-stu-id="9cb55-128">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9cb55-129">Kompilátor vloží do XML standardní název aplikace "MyApplication. app".</span><span class="sxs-lookup"><span data-stu-id="9cb55-129">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="9cb55-130">Toto je alternativní řešení pro povolení spouštění aplikací v systému Windows Server 2003 s aktualizací Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="9cb55-130">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9cb55-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cb55-131">See also</span></span>

- [<span data-ttu-id="9cb55-132">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="9cb55-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9cb55-133">-nowin32manifest (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="9cb55-133">-nowin32manifest (C# Compiler Options)</span></span>](./nowin32manifest-compiler-option.md)
- [<span data-ttu-id="9cb55-134">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="9cb55-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
