---
title: Určení umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646035"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="7f9bf-102">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="7f9bf-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="7f9bf-103">Existují dva způsoby, jak zadat umístění sestavení:</span><span class="sxs-lookup"><span data-stu-id="7f9bf-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="7f9bf-104">Pomocí [\<codeBase>](./file-schema/runtime/codebase-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="7f9bf-105">Pomocí [\<probing>](./file-schema/runtime/probing-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="7f9bf-106">Můžete také použít [konfigurační nástroj .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) k určení umístění sestavení nebo určení umístění pro modul common language runtime pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="7f9bf-107">Použití \<codeBase> elementu</span><span class="sxs-lookup"><span data-stu-id="7f9bf-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="7f9bf-108">Tento element lze použít **\<codeBase>** pouze v souborech zásad konfigurace počítače nebo u souborů zásad vydavatele, které také přesměrují verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="7f9bf-109">Pokud modul runtime určuje, která verze sestavení se má použít, použije základní nastavení kódu ze souboru, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="7f9bf-110">Pokud není uveden žádný základ kódu, sondy runtime pro sestavení normálním způsobem.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="7f9bf-111">Podrobnosti najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7f9bf-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="7f9bf-112">Následující příklad ukazuje, jak určit umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="7f9bf-113">Atribut **Version** je vyžadován pro všechna sestavení se silným názvem, ale měla by být vynechána pro sestavení, která nejsou silně pojmenována.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="7f9bf-114">**\<codeBase>** Element vyžaduje atribut **href** .</span><span class="sxs-lookup"><span data-stu-id="7f9bf-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="7f9bf-115">V elementu nelze zadat rozsahy verzí **\<codeBase>** .</span><span class="sxs-lookup"><span data-stu-id="7f9bf-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f9bf-116">Pokud zadáváte nápovědu k základnímu kódu pro sestavení, které není silně pojmenováno, pomocný parametr musí ukazovat na základ aplikace nebo podadresář základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="7f9bf-117">Použití \<probing> elementu</span><span class="sxs-lookup"><span data-stu-id="7f9bf-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="7f9bf-118">Modul runtime vyhledává sestavení, která nemají základ kódu, pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="7f9bf-119">Další informace o zjišťování najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7f9bf-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="7f9bf-120">Pomocí [\<probing>](./file-schema/runtime/probing-element.md) elementu v konfiguračním souboru aplikace můžete určit podadresáře, které by měl modul runtime při hledání sestavení Hledat.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="7f9bf-121">Následující příklad ukazuje, jak zadat adresáře, které by měl modul runtime Hledat.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="7f9bf-122">Atribut **Nastavení privatePath** obsahuje adresáře, ve kterých by měl modul runtime Hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="7f9bf-123">Pokud je aplikace umístěná v adresáři C:\Program době Files\MyApp, modul runtime bude hledat sestavení, která nespecifikují základ kódu v adresáři C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin a C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="7f9bf-124">Adresáře určené v **Nastavení privatePath** musí být podadresáře základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9bf-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f9bf-125">See also</span></span>

- [<span data-ttu-id="7f9bf-126">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="7f9bf-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="7f9bf-127">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="7f9bf-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="7f9bf-128">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="7f9bf-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="7f9bf-129">Konfigurace aplikací pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="7f9bf-129">Configuring Apps by using Configuration Files</span></span>](index.md)
