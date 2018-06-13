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
ms.openlocfilehash: 3ac2b60b5e638290ea7e17e539519e3a0d355c12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214955"
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="3d718-102">-win32manifest (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="3d718-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="3d718-103">Použití **-win32manifest** možnost zadat vlastní soubor manifestu aplikace Win32, který má být vložen do souboru projektu přenosné spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="3d718-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d718-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d718-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d718-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d718-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="3d718-106">Název a umístění vlastního souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="3d718-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d718-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d718-107">Remarks</span></span>  
 <span data-ttu-id="3d718-108">Ve výchozím nastavení kompilátor Visual C# vloží manifest aplikace, která určuje požadovanou úroveň vykonávání jako "asInvoker".</span><span class="sxs-lookup"><span data-stu-id="3d718-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="3d718-109">Manifest vytvoří ve stejné složce, ve kterém spustitelný soubor je vytvořen, obvykle bin\Debug nebo bin\Release složky při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d718-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="3d718-110">Pokud chcete zadat vlastní manifest, např. Chcete-li určit požadovanou úroveň vykonávání "highestAvailable" nebo "requireAdministrator" pomocí této možnosti můžete zadat název souboru.</span><span class="sxs-lookup"><span data-stu-id="3d718-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d718-111">Tuto možnost a [-win32res (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="3d718-111">This option and the [-win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="3d718-112">Pokud se pokusíte použít obě možnosti ve stejném příkazovém řádku obdržíte chybu sestavení.</span><span class="sxs-lookup"><span data-stu-id="3d718-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="3d718-113">Aplikace, která nemá žádné aplikace, manifest, který určuje že požadovanou úroveň vykonávání budou platit virtualizaci souborů a registrů pod funkci Řízení uživatelských účtů v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3d718-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="3d718-114">Další informace najdete v tématu [řízení uživatelských účtů](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="3d718-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="3d718-115">Aplikace budou platit virtualizace, pokud platí některá z těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="3d718-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="3d718-116">Použijete **-nowin32manifest** a neposkytuje manifest v pozdější fázi sestavování nebo jako součást souboru prostředků Windows (.res) pomocí **-win32res** možnost.</span><span class="sxs-lookup"><span data-stu-id="3d718-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
-   <span data-ttu-id="3d718-117">Můžete zadat vlastní manifestu, který není uveden požadovanou úroveň vykonávání.</span><span class="sxs-lookup"><span data-stu-id="3d718-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="3d718-118">Visual Studio vytvoří výchozí soubor manifest a ukládá je v adresářích debug a release společně se spustitelným souborem.</span><span class="sxs-lookup"><span data-stu-id="3d718-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="3d718-119">Můžete přidat vlastní manifest vytvořením v každém textovém editoru a následným přidáním do projektu.</span><span class="sxs-lookup"><span data-stu-id="3d718-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="3d718-120">Alternativně můžete můžete kliknout pravým tlačítkem **projektu** ikonu v **Průzkumníku řešení**, klikněte na tlačítko **přidat novou položku**a pak klikněte na tlačítko **soubor manifestu aplikace**.</span><span class="sxs-lookup"><span data-stu-id="3d718-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="3d718-121">Po přidání nového nebo existujícího souboru manifestu se zobrazí v **Manifest** rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="3d718-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="3d718-122">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="3d718-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="3d718-123">Manifest aplikace můžete poskytnout jako vlastní krok po sestavení nebo jako součást zdrojového souboru Win32 pomocí [-nowin32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="3d718-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="3d718-124">Stejnou možnost použijte, pokud má vaše aplikace podléhat souborů nebo registru virtualizace v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="3d718-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="3d718-125">To zabrání kompilátoru z vytváření a vložení manifestu výchozí do přenosného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="3d718-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d718-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d718-126">Example</span></span>  
 <span data-ttu-id="3d718-127">Následující příklad ukazuje výchozí manifest, že kompilátor Visual C# vloží do PE.</span><span class="sxs-lookup"><span data-stu-id="3d718-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d718-128">Kompilátor vloží standardní název aplikace "MyApplication.app" do souboru xml.</span><span class="sxs-lookup"><span data-stu-id="3d718-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="3d718-129">Toto je alternativní řešení Chcete-li povolit aplikací pro spuštění na Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="3d718-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d718-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d718-130">See Also</span></span>  
 [<span data-ttu-id="3d718-131">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d718-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="3d718-132">-nowin32manifest (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="3d718-132">-nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [<span data-ttu-id="3d718-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="3d718-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
