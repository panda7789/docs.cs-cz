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
ms.openlocfilehash: f15111fbd65896cc42ab3d1462dc567133a7b4ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566343"
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="d8d8f-102">Určení sestavení&#39;s umístění</span><span class="sxs-lookup"><span data-stu-id="d8d8f-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="d8d8f-103">Existují dva způsoby, jak zadat umístění sestavení:</span><span class="sxs-lookup"><span data-stu-id="d8d8f-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="d8d8f-104">Použití [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="d8d8f-105">Použití [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="d8d8f-106">Můžete také použít [konfiguračního nástroje rozhraní .NET Framework (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) zadat umístění sestavení nebo určit umístění pro modul common language runtime pro sběr dat pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="d8d8f-107">Použití \<codeBase > – Element</span><span class="sxs-lookup"><span data-stu-id="d8d8f-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="d8d8f-108">Můžete použít  **\<codeBase >** element pouze v počítači konfigurace nebo vydavatele zásad souborů, které také přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="d8d8f-109">Když modul runtime určuje verzi sestavení, která se má použít, bude se vztahovat základní nastavení kódu ze souboru, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="d8d8f-110">Pokud je uveden žádný základní kód, testy se modul runtime pro sestavení běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="d8d8f-111">Podrobnosti najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d8d8f-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="d8d8f-112">Následující příklad ukazuje, jak zadat umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="d8d8f-113">**Verze** atribut je vyžadován pro všechna sestavení se silným názvem, ale musí být vynechána pro sestavení, které se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="d8d8f-114"> *\*\<CodeBase >** element vyžaduje *\*href** atribut.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="d8d8f-115">Nelze určit verzi rozsahů v  **\<codeBase >** elementu.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8d8f-116">Pokud pro sestavení, který není silným názvem jsou zadání pomocného parametru základní kód, pomocný parametr musí ukazovat na základ cesty aplikace nebo o podadresář základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="d8d8f-117">Použití \<zjišťování > – Element</span><span class="sxs-lookup"><span data-stu-id="d8d8f-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="d8d8f-118">Běhové prostředí vyhledává sestavení, které nemají základu kódu pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="d8d8f-119">Další informace o zjišťování najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d8d8f-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="d8d8f-120">Můžete použít [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) prvku v konfiguračním souboru aplikace k určení podadresářů, které by měl modul runtime vyhledat při hledání sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="d8d8f-121">Následující příklad ukazuje, jak určit adresáře, který by měl modul runtime vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d8d8f-122">**PrivatePath** atribut obsahuje adresáře, které by měl modul runtime vyhledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="d8d8f-123">Pokud je umístěna na C:\Program Files\MyApp aplikace, modul runtime vyhledá sestavení, která v C:\Program Files\MyApp\Bin C:\Program Files\MyApp\Bin2\Subbin a C:\Program Files\MyApp\Bin3 neurčí základ kódu.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="d8d8f-124">Adresáře určené v **privatePath** musí být základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8d8f-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d8f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8d8f-125">See also</span></span>
- [<span data-ttu-id="d8d8f-126">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="d8d8f-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="d8d8f-127">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="d8d8f-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="d8d8f-128">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="d8d8f-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d8d8f-129">Konfigurace aplikací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8d8f-129">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
