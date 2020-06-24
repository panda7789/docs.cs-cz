---
title: Určení umístění sestavení
description: Viz jak zadat umístění sestavení v rozhraní .NET pomocí elementu codeBase nebo prvku zjišťování v konfiguračním souboru XML.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: e14bdc12598d0aa6cdd2789b09a04ab8ed134169
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141701"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="a4432-103">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="a4432-103">Specifying an Assembly's Location</span></span>
<span data-ttu-id="a4432-104">Existují dva způsoby, jak zadat umístění sestavení:</span><span class="sxs-lookup"><span data-stu-id="a4432-104">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="a4432-105">Pomocí [\<codeBase>](./file-schema/runtime/codebase-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a4432-105">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="a4432-106">Pomocí [\<probing>](./file-schema/runtime/probing-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a4432-106">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="a4432-107">Můžete také použít [konfigurační nástroj .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) k určení umístění sestavení nebo určení umístění pro modul common language runtime pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4432-107">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="a4432-108">Použití \<codeBase> elementu</span><span class="sxs-lookup"><span data-stu-id="a4432-108">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="a4432-109">Tento element lze použít **\<codeBase>** pouze v souborech zásad konfigurace počítače nebo u souborů zásad vydavatele, které také přesměrují verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4432-109">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="a4432-110">Pokud modul runtime určuje, která verze sestavení se má použít, použije základní nastavení kódu ze souboru, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="a4432-110">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="a4432-111">Pokud není uveden žádný základ kódu, sondy runtime pro sestavení normálním způsobem.</span><span class="sxs-lookup"><span data-stu-id="a4432-111">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="a4432-112">Podrobnosti najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a4432-112">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="a4432-113">Následující příklad ukazuje, jak určit umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4432-113">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="a4432-114">Atribut **Version** je vyžadován pro všechna sestavení se silným názvem, ale měla by být vynechána pro sestavení, která nejsou silně pojmenována.</span><span class="sxs-lookup"><span data-stu-id="a4432-114">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="a4432-115">**\<codeBase>** Element vyžaduje atribut **href** .</span><span class="sxs-lookup"><span data-stu-id="a4432-115">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="a4432-116">V elementu nelze zadat rozsahy verzí **\<codeBase>** .</span><span class="sxs-lookup"><span data-stu-id="a4432-116">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4432-117">Pokud zadáváte nápovědu k základnímu kódu pro sestavení, které není silně pojmenováno, pomocný parametr musí ukazovat na základ aplikace nebo podadresář základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4432-117">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="a4432-118">Použití \<probing> elementu</span><span class="sxs-lookup"><span data-stu-id="a4432-118">Using the \<probing> Element</span></span>  
 <span data-ttu-id="a4432-119">Modul runtime vyhledává sestavení, která nemají základ kódu, pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="a4432-119">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="a4432-120">Další informace o zjišťování najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a4432-120">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="a4432-121">Pomocí [\<probing>](./file-schema/runtime/probing-element.md) elementu v konfiguračním souboru aplikace můžete určit podadresáře, které by měl modul runtime při hledání sestavení Hledat.</span><span class="sxs-lookup"><span data-stu-id="a4432-121">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="a4432-122">Následující příklad ukazuje, jak zadat adresáře, které by měl modul runtime Hledat.</span><span class="sxs-lookup"><span data-stu-id="a4432-122">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="a4432-123">Atribut **Nastavení privatePath** obsahuje adresáře, ve kterých by měl modul runtime Hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4432-123">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="a4432-124">Pokud je aplikace umístěná v adresáři C:\Program době Files\MyApp, modul runtime bude hledat sestavení, která nespecifikují základ kódu v adresáři C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin a C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="a4432-124">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="a4432-125">Adresáře určené v **Nastavení privatePath** musí být podadresáře základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4432-125">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4432-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4432-126">See also</span></span>

- [<span data-ttu-id="a4432-127">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="a4432-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="a4432-128">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="a4432-128">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="a4432-129">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="a4432-129">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a4432-130">Konfigurace aplikací pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="a4432-130">Configuring Apps by using Configuration Files</span></span>](index.md)
