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
# <a name="specifying-an-assemblys-location"></a>Určení umístění sestavení
Existují dva způsoby, jak zadat umístění sestavení:  
  
- Pomocí [\<codeBase>](./file-schema/runtime/codebase-element.md) elementu.  
  
- Pomocí [\<probing>](./file-schema/runtime/probing-element.md) elementu.  
  
 Můžete také použít [konfigurační nástroj .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) k určení umístění sestavení nebo určení umístění pro modul common language runtime pro sestavení.  
  
## <a name="using-the-codebase-element"></a>Použití \<codeBase> elementu  
 Tento element lze použít **\<codeBase>** pouze v souborech zásad konfigurace počítače nebo u souborů zásad vydavatele, které také přesměrují verzi sestavení. Pokud modul runtime určuje, která verze sestavení se má použít, použije základní nastavení kódu ze souboru, který určuje verzi. Pokud není uveden žádný základ kódu, sondy runtime pro sestavení normálním způsobem. Podrobnosti najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Následující příklad ukazuje, jak určit umístění sestavení.  
  
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
  
 Atribut **Version** je vyžadován pro všechna sestavení se silným názvem, ale měla by být vynechána pro sestavení, která nejsou silně pojmenována. **\<codeBase>** Element vyžaduje atribut **href** . V elementu nelze zadat rozsahy verzí **\<codeBase>** .  
  
> [!NOTE]
> Pokud zadáváte nápovědu k základnímu kódu pro sestavení, které není silně pojmenováno, pomocný parametr musí ukazovat na základ aplikace nebo podadresář základního adresáře aplikace.  
  
## <a name="using-the-probing-element"></a>Použití \<probing> elementu  
 Modul runtime vyhledává sestavení, která nemají základ kódu, pomocí zjišťování. Další informace o zjišťování najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Pomocí [\<probing>](./file-schema/runtime/probing-element.md) elementu v konfiguračním souboru aplikace můžete určit podadresáře, které by měl modul runtime při hledání sestavení Hledat. Následující příklad ukazuje, jak zadat adresáře, které by měl modul runtime Hledat.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Atribut **Nastavení privatePath** obsahuje adresáře, ve kterých by měl modul runtime Hledat sestavení. Pokud je aplikace umístěná v adresáři C:\Program době Files\MyApp, modul runtime bude hledat sestavení, která nespecifikují základ kódu v adresáři C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin a C:\Program Files\MyApp\Bin3. Adresáře určené v **Nastavení privatePath** musí být podadresáře základního adresáře aplikace.  
  
## <a name="see-also"></a>Viz také

- [Sestavení v .NET](../../standard/assembly/index.md)
- [Programování se sestaveními](../../standard/assembly/index.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací pomocí konfiguračních souborů](index.md)
