---
title: SqlClient pro typy Entity Framework
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: eb12bde1e319fde5adf20ad6cd54f8776aeda31d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147652"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient pro typy Entity Framework
Zprostředkovatel dat .NET Framework pro soubor manifestu zprostředkovatele SQL Server (SqlClient) obsahuje seznam primitivní typy zprostředkovatele omezující vlastnosti pro každý typ mapování mezi koncepční a primitivní typy modelů úložiště a propagační akce a převod pravidla mezi koncepční a úložiště primitivní typy modelu.  
  
 Následující tabulka popisuje typy pro SQL Server 2008, [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], a [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] databází a jak tyto typy mapovány na koncepční model typy. Některé nové typy byly zavedeny v novějších verzích systému SQL Server nejsou podporovány ve starších verzích systému SQL Server. Tyto typy jsou uvedené v následující tabulce.  
  
|Typ zprostředkovatele<br /><br /> name|Typ zprostředkovatele<br /><br /> atributy|`EDMSimpleType`<br /><br /> name|Charakteristiky|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|není k dispozici|`Edm.Boolean`|není k dispozici|  
|`tinyint`|není k dispozici|`Edm.Byte`|není k dispozici|  
|`smallint`|není k dispozici|`Edm.Int16`|není k dispozici|  
|`int`|není k dispozici|`Edm.Int32`|není k dispozici|  
|`bigint`|není k dispozici|`Edm.Int64`|není k dispozici|  
|`float`|není k dispozici|`Edm.Double`|není k dispozici|  
|`real`|není k dispozici|`Edm.Double`|není k dispozici|  
|`decimal`|není k dispozici|`Edm.Decimal`|Přesnost:<br /><br /> – Minimálně: 1<br /><br /> -Maximum: 38<br /><br /> – Výchozí hodnota: 18<br /><br /> -Konstantní: False<br /><br /> Škálování:<br /><br /> – Minimálně: 0<br /><br /> -Maximum: 38<br /><br /> – Výchozí hodnota: 0<br /><br /> -Konstantní: False|  
|`numeric`|není k dispozici|`Edm.Decimal`|Přesnost:<br /><br /> – Minimálně: 1<br /><br /> -Maximum: 38<br /><br /> – Výchozí hodnota: 18<br /><br /> -Konstantní: False<br /><br /> Škálování:<br /><br /> – Minimálně: 0<br /><br /> -Maximum: 38<br /><br /> – Výchozí hodnota: 0<br /><br /> -Konstantní: False|  
|`smallmoney`|není k dispozici|`Edm.Decimal`|Přesnost:<br /><br /> – Výchozí hodnota: 10<br /><br /> -Konstantní: Pravda<br /><br /> Škálování:<br /><br /> – Výchozí hodnota: 4<br /><br /> -Konstantní: Pravda|  
|`money`|není k dispozici|`Edm.Decimal`|Přesnost:<br /><br /> – Výchozí hodnota: 19<br /><br /> -Konstantní: Pravda<br /><br /> Škálování:<br /><br /> – Výchozí hodnota: 4<br /><br /> -Konstantní: Pravda|  
|`binary`|není k dispozici|`Edm.Binary`|MaxLength:<br /><br /> – Minimálně: 1<br /><br /> -Maximum: 8000<br /><br /> – Výchozí hodnota: 8000<br /><br /> -Konstantní: False<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda|  
|`varbinary`|není k dispozici|`Edm.Binary`|MaxLength:<br /><br /> – Minimálně: 1<br /><br /> -Maximum: 8000<br /><br /> – Výchozí hodnota: 8000<br /><br /> -Konstantní: False<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`varbinary(max)`<br /><br /> Poznámka: Tento typ není podporován v [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|není k dispozici|`Edm.Binary`|MaxLength:<br /><br /> – Výchozí hodnota: 214748364780<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`image`|není k dispozici|`Edm.Binary`|MaxLength:<br /><br /> – Výchozí hodnota: 2147483647<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`timestamp`|není k dispozici|`Edm.Binary`|MaxLength:<br /><br /> – Výchozí hodnota: 8<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda|  
|`rowversion`|není k dispozici|`Edm.Binary`|MaxLength:<br /><br /> – Výchozí hodnota: 8<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda|  
|`smalldatetime`|není k dispozici|`Edm.DateTime`|Přesnost:<br /><br /> – Výchozí hodnota: 0<br /><br /> -Konstantní: Pravda|  
|`datetime`|není k dispozici|`Edm.DateTime`|Přesnost:<br /><br /> – Výchozí hodnota: 3<br /><br /> -Konstantní: Pravda|  
|`date`<br /><br /> Poznámka: Tento typ není podporován v systému SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTime`|Přesnost:<br /><br /> – Výchozí hodnota: 0<br /><br /> -Konstantní: False|  
|`time`<br /><br /> Poznámka: Tento typ není podporován v systému SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.Time`|Přesnost:<br /><br /> – Výchozí hodnota: 7<br /><br /> -Konstantní: False|  
|`datetime2`<br /><br /> Poznámka: Tento typ není podporován v systému SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTime`|Přesnost:<br /><br /> – Výchozí hodnota: 7<br /><br /> -Konstantní: False|  
|`datetimeoffset`<br /><br /> Poznámka: Tento typ není podporován v systému SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTimeOffset`|Přesnost:<br /><br /> – Výchozí hodnota: 7<br /><br /> -Konstantní: False|  
|`nvarchar`<br /><br /> Poznámka: Tento typ není podporován v [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|není k dispozici|`Edm.String`|MaxLength:<br /><br /> – Minimálně: 1<br /><br /> -Maximum: 4000<br /><br /> – Výchozí hodnota: 4000<br /><br /> -Konstantní: False<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`varchar`<br /><br /> Poznámka: Tento typ není podporován v [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|není k dispozici|`Edm.String`|MaxLength:<br /><br /> – Minimálně: 1<br /><br /> -Maximum: 8000<br /><br /> – Výchozí hodnota: 8000<br /><br /> -Konstantní: False<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`char`|není k dispozici|`Edm.String`|MaxLength:<br /><br /> – Minimálně: 1<br /><br /> -Maximum: 8000<br /><br /> – Výchozí hodnota: 8000<br /><br /> -Konstantní: False<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda|  
|`nchar`|není k dispozici|`Edm.String`|MaxLength:<br /><br /> – Minimálně: 1<br /><br /> -Maximum: 4000<br /><br /> – Výchozí hodnota: 4000<br /><br /> -Konstantní: False<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda|  
|`varchar`(`max`)|není k dispozici|`Edm.String`|MaxLength:<br /><br /> – Výchozí hodnota: 2147483647<br /><br /> -Konstantní: Pravda<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`nvarchar`(`max`)|není k dispozici|`Edm.String`|MaxLength:<br /><br /> – Výchozí hodnota: 1073741823<br /><br /> -Konstantní: Pravda<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`ntext`|Stejné srovnatelné: False<br /><br /> Porovnatelný z hlediska pořadí: False|`Edm.String`|MaxLength:<br /><br /> – Výchozí hodnota: 1073741823<br /><br /> -Konstantní: Pravda<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`text`|Stejné srovnatelné: False<br /><br /> Porovnatelný z hlediska pořadí: False|`Edm.String`|MaxLength:<br /><br /> – Výchozí hodnota: 2147483647<br /><br /> -Konstantní: Pravda<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
|`Unique`<br /><br /> `identifier`|Stejné srovnatelné: Pravda<br /><br /> Porovnatelný z hlediska pořadí: Pravda|`Edm.Guid`|není k dispozici|  
|`xml`|Stejné srovnatelné: False<br /><br /> Porovnatelný z hlediska pořadí: False|`Edm.String`|MaxLength:<br /><br /> – Výchozí hodnota: 1073741823<br /><br /> -Konstantní: Pravda<br /><br /> Unicode:<br /><br /> – Výchozí hodnota: Pravda<br /><br /> -Konstantní: Pravda<br /><br /> FixedLength:<br /><br /> – Výchozí hodnota: False<br /><br /> -Konstantní: Pravda|  
  
## <a name="see-also"></a>Viz také:

- [Specifikace CSDL, SSDL a MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
