---
title: 'Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH'
description: Otestujte správné fungování sdíleného sestavení s mnoha aplikacemi v rozhraní .NET pomocí konfiguračního souboru XML počítače a proměnné prostředí mechanismu DEVPATH.
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 50b61eedddabd660b1834565a61738f460ae9ff9
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105376"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH
Vývojáři mohou chtít zajistit, aby sdílené sestavení, které sestavuje, fungovalo správně s více aplikacemi. Namísto průběžného vkládání sestavení do globální mezipaměti sestavení (GAC) během cyklu vývoje může vývojář vytvořit proměnnou prostředí mechanismu DEVPATH, která odkazuje na výstupní adresář sestavení pro sestavení.  
  
 Předpokládejme například, že vytváříte sdílené sestavení s názvem MySharedAssembly a výstupní adresář je C:\MySharedAssembly\Debug. C:\MySharedAssembly\Debug můžete umístit do proměnné mechanismu DEVPATH. Pak je nutné zadat [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) prvek v konfiguračním souboru počítače. Tento prvek oznamuje modulu CLR (Common Language Runtime), aby mohl používat mechanismu DEVPATH k vyhledávání sestavení.  
  
 Sdílené sestavení musí být zjistitelné modulem runtime.  Chcete-li určit privátní adresář pro překlad odkazů na sestavení, použijte [ \<codeBase> element](./file-schema/runtime/codebase-element.md) nebo [ \<probing> element](./file-schema/runtime/probing-element.md) v konfiguračním souboru, jak je popsáno v tématu [určení umístění sestavení](specify-assembly-location.md).  Můžete také vložit sestavení do podadresáře adresáře aplikace. Další informace najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
> Jedná se o pokročilou funkci, která je určená jenom pro vývoj.  
  
 Následující příklad ukazuje, jak způsobit, aby modul runtime vyhledal sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Toto nastavení má výchozí hodnotu NEPRAVDA.  
  
> [!NOTE]
> Toto nastavení použijte pouze v době vývoje. Modul runtime nekontroluje verze v sestaveních se silným názvem nalezenými v mechanismu DEVPATH. Jednoduše používá první nalezené sestavení.  
  
## <a name="see-also"></a>Viz také

- [Konfigurace aplikací pomocí konfiguračních souborů](index.md)
