---
title: Element <developmentMode>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117622"
---
# <a name="developmentmode-element"></a>\<element > developmentMode
Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentMode >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**developerInstallation**|Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**true**|Vyhledá sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.|  
|**false**|Nehledá sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH. Toto je výchozí nastavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Toto nastavení použijte pouze v době vývoje. Modul runtime nekontroluje verze v sestaveních se silným názvem nalezenými v mechanismu DEVPATH. Jednoduše používá první nalezené sestavení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak způsobit, aby modul runtime vyhledal sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH](../../how-to-locate-assemblies-by-using-devpath.md)
