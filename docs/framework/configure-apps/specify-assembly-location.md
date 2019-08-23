---
title: Určení umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 43cd1d0edbb607f69f27661aae3372e93564b3b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932338"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="d7743-102">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="d7743-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="d7743-103">Existují dva způsoby, jak zadat umístění sestavení:</span><span class="sxs-lookup"><span data-stu-id="d7743-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="d7743-104">Pomocí elementu [> základukódu.\<](./file-schema/runtime/codebase-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7743-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="d7743-105">Použití prvku > zjišťování. [ \<](./file-schema/runtime/probing-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7743-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="d7743-106">Můžete také použít [konfigurační nástroj .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) k určení umístění sestavení nebo určení umístění pro modul common language runtime pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7743-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="d7743-107">Použití elementu > codebase \<</span><span class="sxs-lookup"><span data-stu-id="d7743-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="d7743-108">Pomocí elementu  **\<> základu kódu** můžete použít pouze soubory zásad pro konfiguraci počítače nebo vydavatele, které také přesměrují verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7743-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="d7743-109">Pokud modul runtime určuje, která verze sestavení se má použít, použije základní nastavení kódu ze souboru, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="d7743-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="d7743-110">Pokud není uveden žádný základ kódu, sondy runtime pro sestavení normálním způsobem.</span><span class="sxs-lookup"><span data-stu-id="d7743-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="d7743-111">Podrobnosti najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d7743-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="d7743-112">Následující příklad ukazuje, jak určit umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7743-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="d7743-113">Atribut **Version** je vyžadován pro všechna sestavení se silným názvem, ale měla by být vynechána pro sestavení, která nejsou silně pojmenována.</span><span class="sxs-lookup"><span data-stu-id="d7743-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="d7743-114">**\<CodeBase>** element vyžaduje **href** atribut.</span><span class="sxs-lookup"><span data-stu-id="d7743-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="d7743-115">**V\<elementu > codebase** nelze zadat rozsahy verzí.</span><span class="sxs-lookup"><span data-stu-id="d7743-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7743-116">Pokud zadáváte nápovědu k základnímu kódu pro sestavení, které není silně pojmenováno, pomocný parametr musí ukazovat na základ aplikace nebo podadresář základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="d7743-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="d7743-117">\<Použití elementu >ho zjišťování</span><span class="sxs-lookup"><span data-stu-id="d7743-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="d7743-118">Modul runtime vyhledává sestavení, která nemají základ kódu, pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d7743-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="d7743-119">Další informace o zjišťování najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d7743-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="d7743-120">Pomocí elementu >ho zjišťování v konfiguračním souboru aplikace můžete určit podadresáře, které by měl modul runtime při hledání sestavení vyhledat. [ \<](./file-schema/runtime/probing-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7743-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="d7743-121">Následující příklad ukazuje, jak zadat adresáře, které by měl modul runtime Hledat.</span><span class="sxs-lookup"><span data-stu-id="d7743-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d7743-122">Atribut **Nastavení privatePath** obsahuje adresáře, ve kterých by měl modul runtime Hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7743-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="d7743-123">Pokud je aplikace umístěná v adresáři C:\Program době Files\MyApp, modul runtime bude hledat sestavení, která nespecifikují základ kódu v adresáři C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin a C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="d7743-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="d7743-124">Adresáře určené v **Nastavení privatePath** musí být podadresáře základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="d7743-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7743-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7743-125">See also</span></span>

- [<span data-ttu-id="d7743-126">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="d7743-126">Assemblies in the Common Language Runtime</span></span>](../app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="d7743-127">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="d7743-127">Programming with Assemblies</span></span>](../app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="d7743-128">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="d7743-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d7743-129">Konfigurace aplikací pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="d7743-129">Configuring Apps by using Configuration Files</span></span>](index.md)
