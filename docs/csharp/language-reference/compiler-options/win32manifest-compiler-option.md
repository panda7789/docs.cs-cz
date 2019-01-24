---
title: -win32manifest (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 9718febfe5aefba75decc133ad2113b64e4547de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618074"
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="71ff0-102">-win32manifest (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="71ff0-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="71ff0-103">Použití **-win32manifest** možnost určit uživatelský soubor manifestu aplikace Win32, který má být vložen do projektu soubor (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="71ff0-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71ff0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71ff0-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="71ff0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="71ff0-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="71ff0-106">Název a umístění vlastního souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="71ff0-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71ff0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71ff0-107">Remarks</span></span>  
 <span data-ttu-id="71ff0-108">Ve výchozím nastavení kompilátor Visual C# vloží manifest aplikace, který určuje požadovanou úroveň spuštění "asInvoker".</span><span class="sxs-lookup"><span data-stu-id="71ff0-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="71ff0-109">Manifest vytvoří ve stejné složce, ve kterém spustitelný soubor vytvořen, obvykle bin\Debug nebo bin\Release složky, pokud používáte sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71ff0-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="71ff0-110">Pokud chcete zadat vlastní manifest, třeba když chcete požadovanou úroveň spuštění "highestAvailable" nebo "requireAdministrator", zadejte tuto možnost použijte k zadání názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="71ff0-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71ff0-111">Tuto možnost a [-win32res (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) možnost se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="71ff0-111">This option and the [-win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="71ff0-112">Pokud se pokusíte použít obě možnosti jsou ve stejném příkazovém řádku se zobrazí chybu sestavení.</span><span class="sxs-lookup"><span data-stu-id="71ff0-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="71ff0-113">Aplikace nemá žádné aplikace, manifest, který určuje, že že požadovanou úroveň spuštění bude v souladu s virtualizací souborů nebo registru pod funkci Řízení uživatelských účtů ve Windows.</span><span class="sxs-lookup"><span data-stu-id="71ff0-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="71ff0-114">Další informace najdete v tématu [řízení uživatelských účtů](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="71ff0-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="71ff0-115">Vaše aplikace bude v souladu s virtualizace, pokud platí některá z těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="71ff0-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="71ff0-116">Použijete **-nowin32manifest** a neposkytuje manifest v pozdějším kroku sestavení nebo jako součást souboru prostředků (.res) Windows s použitím **-win32res** možnost.</span><span class="sxs-lookup"><span data-stu-id="71ff0-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
-   <span data-ttu-id="71ff0-117">Poskytnete vlastního manifestu, která neurčuje požadovanou úroveň spuštění.</span><span class="sxs-lookup"><span data-stu-id="71ff0-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="71ff0-118">Visual Studio vytvoří výchozí soubor .manifest a ukládá ho do adresáře debug a release spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="71ff0-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="71ff0-119">Vytvoření nového v libovolném textovém editoru a následným přidáním souboru do projektu můžete přidat vlastní manifest.</span><span class="sxs-lookup"><span data-stu-id="71ff0-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="71ff0-120">Alternativně je můžete kliknout pravým tlačítkem **projektu** ikonu **Průzkumníku řešení**, klikněte na tlačítko **přidat novou položku**a potom klikněte na tlačítko **soubor manifestu aplikace**.</span><span class="sxs-lookup"><span data-stu-id="71ff0-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="71ff0-121">Po přidání nového nebo existujícího souboru manifestu, se zobrazí v **Manifest** rozevírací seznam.</span><span class="sxs-lookup"><span data-stu-id="71ff0-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="71ff0-122">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="71ff0-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="71ff0-123">Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást soubor prostředků Win32 pomocí [-nowin32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="71ff0-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="71ff0-124">Stejnou možnost použijte, pokud chcete, aby byla v souladu s virtualizací souborů nebo registru v systému Windows Vista aplikace.</span><span class="sxs-lookup"><span data-stu-id="71ff0-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="71ff0-125">To zabrání kompilátoru od vytvoření a vkládání výchozí manifest do přenosného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="71ff0-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71ff0-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="71ff0-126">Example</span></span>  
 <span data-ttu-id="71ff0-127">Následující příklad ukazuje výchozí manifest, že kompilátor Visual C# vloží do PE.</span><span class="sxs-lookup"><span data-stu-id="71ff0-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71ff0-128">Kompilátor vloží název standardní aplikace "MyApplication.app" do souboru xml.</span><span class="sxs-lookup"><span data-stu-id="71ff0-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="71ff0-129">Toto je alternativní řešení Chcete-li povolit aplikace, které poběží na Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="71ff0-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71ff0-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71ff0-130">See also</span></span>

- [<span data-ttu-id="71ff0-131">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71ff0-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="71ff0-132">-nowin32manifest (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="71ff0-132">-nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)
- [<span data-ttu-id="71ff0-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="71ff0-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
