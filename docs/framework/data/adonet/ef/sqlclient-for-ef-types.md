---
title: SqlClient pro Entity FrameworkTypes
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: f5b471cea4f26c06e8af77298c256bff97ef21de
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766540"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient pro Entity FrameworkTypes
Zprostředkovatel dat .NET Framework pro soubor manifestu zprostředkovatele SQL Server (SqlClient) obsahuje seznam primitivní typy zprostředkovatele omezující vlastnosti pro každý typ mapování mezi koncepční a primitivních typů modelu úložiště a povýšení a převod pravidla mezi typy primitivní modelu koncepční a úložiště.  
  
 Následující tabulka popisuje typy pro SQL Server 2008, [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], a [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] databáze a jak tyto typy mapovány na konceptuální model typy. Některé nové typy byly zavedeny v novějších verzích systému SQL Server nejsou podporovány ve starších verzích systému SQL Server. Tyto typy jsou uvedené v následující tabulce.  
  
|Typ zprostředkovatele<br /><br /> name|Typ zprostředkovatele<br /><br /> atributy|`EDMSimpleType`<br /><br /> name|Charakteristiky|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|není k dispozici|`Edm.Boolean`|není k dispozici|  
|`tinyint`|není k dispozici|`Edm.Byte`|není k dispozici|  
|`smallint`|není k dispozici|`Edm.Int16`|není k dispozici|  
|`int`|není k dispozici|`Edm.Int32`|není k dispozici|  
|`bigint`|není k dispozici|`Edm.Int64`|není k dispozici|  
|`float`|není k dispozici|`Edm.Double`|není k dispozici|  
|`real`|není k dispozici|`Edm.Double`|není k dispozici|  
|`decimal`|není k dispozici|`Edm.Decimal`|Přesnost:<br /><br /> -Minimální: 1<br /><br /> -Maximální: 38<br /><br /> -Výchozí: 18<br /><br /> -Konstantní: False<br /><br /> Škálování:<br /><br /> -Minimální: 0<br /><br /> -Maximální: 38<br /><br /> -Výchozí: 0<br /><br /> -Konstantní: False|  
|`numeric`|není k dispozici|`Edm.Decimal`|Přesnost:<br /><br /> -Minimální: 1<br /><br /> -Maximální: 38<br /><br /> -Výchozí: 18<br /><br /> -Konstantní: False<br /><br /> Škálování:<br /><br /> -Minimální: 0<br /><br /> -Maximální: 38<br /><br /> -Výchozí: 0<br /><br /> -Konstantní: False|  
|`smallmoney`|není k dispozici|`Edm.Decimal`|Přesnost:<br /><br /> -Výchozí: 10<br /><br /> -Konstantní: True<br /><br /> Škálování:<br /><br /> -Výchozí: 4<br /><br /> -Konstantní: True|  
|`money`|není k dispozici|`Edm.Decimal`|Přesnost:<br /><br /> -Výchozí: 19<br /><br /> -Konstantní: True<br /><br /> Škálování:<br /><br /> -Výchozí: 4<br /><br /> -Konstantní: True|  
|`binary`|není k dispozici|`Edm.Binary`|Hodnota MaxLength:<br /><br /> -Minimální: 1<br /><br /> -Maximální: 8000<br /><br /> -Výchozí: 8000<br /><br /> -Konstantní: False<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True|  
|`varbinary`|není k dispozici|`Edm.Binary`|Hodnota MaxLength:<br /><br /> -Minimální: 1<br /><br /> -Maximální: 8000<br /><br /> -Výchozí: 8000<br /><br /> -Konstantní: False<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`varbinary(max)`<br /><br /> Poznámka: Tento typ není podporován v [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|není k dispozici|`Edm.Binary`|Hodnota MaxLength:<br /><br /> -Výchozí: 214748364780<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`image`|není k dispozici|`Edm.Binary`|Hodnota MaxLength:<br /><br /> -Výchozí: 2147483647.<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`timestamp`|není k dispozici|`Edm.Binary`|Hodnota MaxLength:<br /><br /> -Výchozí: 8<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True|  
|`rowversion`|není k dispozici|`Edm.Binary`|Hodnota MaxLength:<br /><br /> -Výchozí: 8<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True|  
|`smalldatetime`|není k dispozici|`Edm.DateTime`|Přesnost:<br /><br /> -Výchozí: 0<br /><br /> -Konstantní: True|  
|`datetime`|není k dispozici|`Edm.DateTime`|Přesnost:<br /><br /> -Výchozí: 3<br /><br /> -Konstantní: True|  
|`date`<br /><br /> Poznámka: Tento typ není podporován v systému SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTime`|Přesnost:<br /><br /> -Výchozí: 0<br /><br /> -Konstantní: False|  
|`time`<br /><br /> Poznámka: Tento typ není podporován v systému SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.Time`|Přesnost:<br /><br /> -Výchozí: 7<br /><br /> -Konstantní: False|  
|`datetime2`<br /><br /> Poznámka: Tento typ není podporován v systému SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTime`|Přesnost:<br /><br /> -Výchozí: 7<br /><br /> -Konstantní: False|  
|`datetimeoffset`<br /><br /> Poznámka: Tento typ není podporován v systému SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTimeOffset`|Přesnost:<br /><br /> -Výchozí: 7<br /><br /> -Konstantní: False|  
|`nvarchar`<br /><br /> Poznámka: Tento typ není podporován v [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|není k dispozici|`Edm.String`|Hodnota MaxLength:<br /><br /> -Minimální: 1<br /><br /> -Maximální: 4000<br /><br /> -Výchozí: 4000<br /><br /> -Konstantní: False<br /><br /> Unicode:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`varchar`<br /><br /> Poznámka: Tento typ není podporován v [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|není k dispozici|`Edm.String`|Hodnota MaxLength:<br /><br /> -Minimální: 1<br /><br /> -Maximální: 8000<br /><br /> -Výchozí: 8000<br /><br /> -Konstantní: False<br /><br /> Unicode:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`char`|není k dispozici|`Edm.String`|Hodnota MaxLength:<br /><br /> -Minimální: 1<br /><br /> -Maximální: 8000<br /><br /> -Výchozí: 8000<br /><br /> -Konstantní: False<br /><br /> Unicode:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True|  
|`nchar`|není k dispozici|`Edm.String`|Hodnota MaxLength:<br /><br /> -Minimální: 1<br /><br /> -Maximální: 4000<br /><br /> -Výchozí: 4000<br /><br /> -Konstantní: False<br /><br /> Unicode:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True|  
|`varchar`(`max`)|není k dispozici|`Edm.String`|Hodnota MaxLength:<br /><br /> -Výchozí: 2147483647.<br /><br /> -Konstantní: True<br /><br /> Unicode:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`nvarchar`(`max`)|není k dispozici|`Edm.String`|Hodnota MaxLength:<br /><br /> -Výchozí: 1073741823<br /><br /> -Konstantní: True<br /><br /> Unicode:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`ntext`|Porovnatelný z hlediska rovnosti: False<br /><br /> Porovnatelný z hlediska pořadí: False|`Edm.String`|Hodnota MaxLength:<br /><br /> -Výchozí: 1073741823<br /><br /> -Konstantní: True<br /><br /> Unicode:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`text`|Porovnatelný z hlediska rovnosti: False<br /><br /> Porovnatelný z hlediska pořadí: False|`Edm.String`|Hodnota MaxLength:<br /><br /> -Výchozí: 2147483647.<br /><br /> -Konstantní: True<br /><br /> Unicode:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
|`Unique`<br /><br /> `identifier`|Porovnatelný z hlediska rovnosti: True<br /><br /> Porovnatelný z hlediska pořadí: True|`Edm.Guid`|není k dispozici|  
|`xml`|Porovnatelný z hlediska rovnosti: False<br /><br /> Porovnatelný z hlediska pořadí: False|`Edm.String`|Hodnota MaxLength:<br /><br /> -Výchozí: 1073741823<br /><br /> -Konstantní: True<br /><br /> Unicode:<br /><br /> -Výchozí: True<br /><br /> -Konstantní: True<br /><br /> Řetězci FixedLength:<br /><br /> -Výchozí: False<br /><br /> -Konstantní: True|  
  
## <a name="see-also"></a>Viz také  
 [Specifikace CSDL, SSDL a MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
