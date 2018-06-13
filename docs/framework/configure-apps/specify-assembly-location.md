---
title: Určení sestavení&#39;s umístění
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 65bd075115e33486e86e8081b01b96db665e9da5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758266"
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="b135c-102">Určení sestavení&#39;s umístění</span><span class="sxs-lookup"><span data-stu-id="b135c-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="b135c-103">K určení umístění sestavení dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="b135c-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="b135c-104">Pomocí [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="b135c-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="b135c-105">Pomocí [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="b135c-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="b135c-106">Můžete také [rozhraní .NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) a zadejte umístění sestavení nebo zadejte umístění pro modul CLR do testů pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="b135c-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="b135c-107">Pomocí \<codeBase > elementu</span><span class="sxs-lookup"><span data-stu-id="b135c-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="b135c-108">Můžete použít  **\<codeBase >** element pouze v počítači konfigurace nebo vydavatele soubory zásad, které také přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="b135c-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="b135c-109">Když modul runtime určuje, které verze sestavení se má použít, bude se vztahovat základní nastavení kódu ze souboru, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="b135c-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="b135c-110">Pokud je uvedené žádné základu kódu, sondy modulu runtime pro sestavení běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="b135c-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="b135c-111">Podrobnosti najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b135c-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="b135c-112">Následující příklad ukazuje, jak k určení umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="b135c-112">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="b135c-113">**Verze** atribut je požadován pro všechny sestavení se silným názvem však by měl být vynechán pro sestavení, které nejsou silným názvem.</span><span class="sxs-lookup"><span data-stu-id="b135c-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="b135c-114">**\<CodeBase >** prvek vyžaduje **href** atribut.</span><span class="sxs-lookup"><span data-stu-id="b135c-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="b135c-115">Nelze zadat rozsahy verze v  **\<codeBase >** element.</span><span class="sxs-lookup"><span data-stu-id="b135c-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b135c-116">Pokud jsou poskytuje základní nápovědu kód pro sestavení, které není silným názvem, pomocný parametr musí odkazovat na základní aplikace a podadresář základnímu adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="b135c-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="b135c-117">Pomocí \<zjišťování > elementu</span><span class="sxs-lookup"><span data-stu-id="b135c-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="b135c-118">Běhové prostředí vyhledává sestavení, které nemají základu kódu pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="b135c-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="b135c-119">Další informace o zjišťování naleznete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b135c-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="b135c-120">Můžete použít [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element v konfiguračním souboru aplikace k určení podadresáře modulu runtime by měli vyhledat při vyhledání sestavení.</span><span class="sxs-lookup"><span data-stu-id="b135c-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="b135c-121">Následující příklad ukazuje, jak zadat adresáře, který by měl hledání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b135c-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="b135c-122">**PrivatePath** atribut obsahuje adresáře, které modul runtime program hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="b135c-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="b135c-123">Pokud aplikace se nachází v C:\Program Files\MyApp, modul runtime bude hledat sestavení, které neurčují C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin a C:\Program Files\MyApp\Bin3 základu kódu.</span><span class="sxs-lookup"><span data-stu-id="b135c-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="b135c-124">Adresáře, určené v **privatePath** musí být základní adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="b135c-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b135c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b135c-125">See Also</span></span>  
 [<span data-ttu-id="b135c-126">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="b135c-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="b135c-127">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="b135c-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="b135c-128">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="b135c-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="b135c-129">Konfigurace aplikací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b135c-129">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
