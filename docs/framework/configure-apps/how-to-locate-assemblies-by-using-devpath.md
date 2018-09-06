---
title: 'Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9b8e3c89c13e7f5c294afca54af7f63293653e87
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788874"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH
Vývojáři mohou chtít mít jistotu, sdílené sestavení, které navíc teď připravují funguje správně s několika aplikacemi. Namísto vložení sestavení do globální mezipaměti sestavení průběžně během cyklu vývoje, můžete vytvořit vývojář proměnné prostředí DEVPATH, který odkazuje na výstupního adresáře sestavení pro sestavení.  
  
 Předpokládejme například, že vytváříte sdílené sestavení nazvané MySharedAssembly a výstupní adresář je C:\MySharedAssembly\Debug. Můžete vložit C:\MySharedAssembly\Debug DEVPATH proměnné. Musíte zadat [ \<developmentmode – >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) prvku v konfiguračním souboru počítače. Tento prvek říká vyhledání sestavení pomocí mechanismu DEVPATH common language runtime.  
  
 Sdílená sestavení musí být zjistitelné modulem runtime.  K určení privátní adresář pro řešení pomocí odkazů na sestavení [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) nebo [ \<zjišťování > Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) v konfiguračním souboru, jak je popsáno v [Určení umístění sestavení](../../../docs/framework/configure-apps/specify-assembly-location.md).  Můžete také vložit sestavení v podadresáři adresáře aplikace. Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Jde o pokročilou funkci určené pouze pro vývoj.  
  
 Následující příklad ukazuje, jak mají hledat sestavení v adresářích určených proměnnou prostředí DEVPATH pomocí běhového modulu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Toto nastavení výchozí hodnota je false.  
  
> [!NOTE]
>  Toto nastavení použijte jenom v době vývoje. Modul runtime verze sestavení se silným názvem součástí mechanismu DEVPATH nekontroluje. Jednoduše použije první sestavení, které nalezne.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace aplikací .NET Framework](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
