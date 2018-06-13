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
# <a name="specifying-an-assembly39s-location"></a>Určení sestavení&#39;s umístění
K určení umístění sestavení dvěma způsoby:  
  
-   Pomocí [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.  
  
-   Pomocí [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.  
  
 Můžete také [rozhraní .NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) a zadejte umístění sestavení nebo zadejte umístění pro modul CLR do testů pro sestavení.  
  
## <a name="using-the-codebase-element"></a>Pomocí \<codeBase > elementu  
 Můžete použít  **\<codeBase >** element pouze v počítači konfigurace nebo vydavatele soubory zásad, které také přesměrování verze sestavení. Když modul runtime určuje, které verze sestavení se má použít, bude se vztahovat základní nastavení kódu ze souboru, který určuje verzi. Pokud je uvedené žádné základu kódu, sondy modulu runtime pro sestavení běžným způsobem. Podrobnosti najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Následující příklad ukazuje, jak k určení umístění sestavení.  
  
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
  
 **Verze** atribut je požadován pro všechny sestavení se silným názvem však by měl být vynechán pro sestavení, které nejsou silným názvem. **\<CodeBase >** prvek vyžaduje **href** atribut. Nelze zadat rozsahy verze v  **\<codeBase >** element.  
  
> [!NOTE]
>  Pokud jsou poskytuje základní nápovědu kód pro sestavení, které není silným názvem, pomocný parametr musí odkazovat na základní aplikace a podadresář základnímu adresáři aplikace.  
  
## <a name="using-the-probing-element"></a>Pomocí \<zjišťování > elementu  
 Běhové prostředí vyhledává sestavení, které nemají základu kódu pomocí zjišťování. Další informace o zjišťování naleznete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Můžete použít [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element v konfiguračním souboru aplikace k určení podadresáře modulu runtime by měli vyhledat při vyhledání sestavení. Následující příklad ukazuje, jak zadat adresáře, který by měl hledání modulu runtime.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath** atribut obsahuje adresáře, které modul runtime program hledat sestavení. Pokud aplikace se nachází v C:\Program Files\MyApp, modul runtime bude hledat sestavení, které neurčují C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin a C:\Program Files\MyApp\Bin3 základu kódu. Adresáře, určené v **privatePath** musí být základní adresáře aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurace aplikací rozhraní .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
