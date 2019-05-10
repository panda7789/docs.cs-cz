---
title: Určení umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 1bfa0ddbeba7546044a0d1ed15f4c2ff303b1491
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583636"
---
# <a name="specifying-an-assemblys-location"></a>Určení umístění sestavení
Existují dva způsoby, jak zadat umístění sestavení:  
  
- Použití [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.  
  
- Použití [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu.  
  
 Můžete také použít [konfiguračního nástroje rozhraní .NET Framework (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) zadat umístění sestavení nebo určit umístění pro modul common language runtime pro sběr dat pro sestavení.  
  
## <a name="using-the-codebase-element"></a>Použití \<codeBase > – Element  
 Můžete použít  **\<codeBase >** element pouze v počítači konfigurace nebo vydavatele zásad souborů, které také přesměrování verze sestavení. Když modul runtime určuje verzi sestavení, která se má použít, bude se vztahovat základní nastavení kódu ze souboru, který určuje verzi. Pokud je uveden žádný základní kód, testy se modul runtime pro sestavení běžným způsobem. Podrobnosti najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Následující příklad ukazuje, jak zadat umístění sestavení.  
  
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
  
 **Verze** atribut je vyžadován pro všechna sestavení se silným názvem, ale musí být vynechána pro sestavení, které se silným názvem.  **\<CodeBase >** element vyžaduje **href** atribut. Nelze určit verzi rozsahů v  **\<codeBase >** elementu.  
  
> [!NOTE]
>  Pokud pro sestavení, který není silným názvem jsou zadání pomocného parametru základní kód, pomocný parametr musí ukazovat na základ cesty aplikace nebo o podadresář základního adresáře aplikace.  
  
## <a name="using-the-probing-element"></a>Použití \<zjišťování > – Element  
 Běhové prostředí vyhledává sestavení, které nemají základu kódu pomocí zjišťování. Další informace o zjišťování najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Můžete použít [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) prvku v konfiguračním souboru aplikace k určení podadresářů, které by měl modul runtime vyhledat při hledání sestavení. Následující příklad ukazuje, jak určit adresáře, který by měl modul runtime vyhledat.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath** atribut obsahuje adresáře, které by měl modul runtime vyhledat sestavení. Pokud je umístěna na C:\Program Files\MyApp aplikace, modul runtime vyhledá sestavení, která v C:\Program Files\MyApp\Bin C:\Program Files\MyApp\Bin2\Subbin a C:\Program Files\MyApp\Bin3 neurčí základ kódu. Adresáře určené v **privatePath** musí být základního adresáře aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací pomocí konfiguračních souborů](index.md)
