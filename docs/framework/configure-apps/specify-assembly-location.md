---
title: Určení umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646035"
---
# <a name="specifying-an-assemblys-location"></a>Určení umístění sestavení
Umístění sestavení lze zadat dvěma způsoby:  
  
- Použití [ \<elementu codeBase>.](./file-schema/runtime/codebase-element.md)  
  
- Použití [ \<sondování>](./file-schema/runtime/probing-element.md) prvek.  
  
 Můžete také použít [nástroj konfigurace rozhraní .NET Framework (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) k určení umístění sestavení nebo k určení umístění pro běžný jazyk runtime pro sondování sestavení.  
  
## <a name="using-the-codebase-element"></a>Použití \<elementu codeBase>  
 CodeBase>prvek můžete použít pouze v konfiguraci počítače nebo v souborech zásad vydavatele, které také přesměrovává verzi sestavení. ** \<** Když runtime určuje, kterou verzi sestavení použít, použije základní nastavení kódu ze souboru, který určuje verzi. Pokud není uveden žádný základ kódu, runtime sondy pro sestavení normálním způsobem. Podrobnosti naleznete [v tématu How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).  
  
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
  
 Atribut **verze** je vyžadován pro všechna sestavení se silným názvem, ale měl by být vynechán pro sestavení, která nejsou silně pojmenované. Element ** \<codeBase>** vyžaduje atribut **href.** V elementu ** \<codeBase>** nelze zadat rozsahy verzí.  
  
> [!NOTE]
> Pokud dodáváte základní nápovědu kódu pro sestavení, které není silně pojmenované, musí nápověda ukazovat na základnu aplikace nebo podadresář základního adresáře aplikace.  
  
## <a name="using-the-probing-element"></a>Použití \<sondování> element  
 Runtime vyhledá sestavení, které nemají základ kódu zjišťováním. Další informace o zjišťování naleznete [v tématu How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Pomocí [ \<prvku sondování>](./file-schema/runtime/probing-element.md) v konfiguračním souboru aplikace můžete určit podadresáře, které by měl runtime hledat při vyhledání sestavení. Následující příklad ukazuje, jak určit adresáře, které by měl zaběhu hledat.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Atribut **privatePath** obsahuje adresáře, které by měl za běhu hledat sestavení. Pokud je aplikace umístěna v c:\programových souborech\MyApp, bude za běhu hledat sestavení, která neurčují základní kód v c:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin\Bin2\Subbin a C:\Program Files\MyApp\Bin3. Adresáře zadané v **privatePath** musí být podadresáře základního adresáře aplikace.  
  
## <a name="see-also"></a>Viz také

- [Sestavení v .NET](../../standard/assembly/index.md)
- [Programování se sestaveními](../../standard/assembly/index.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací pomocí konfiguračních souborů](index.md)
