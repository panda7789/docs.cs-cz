---
title: SqlClient pro typy Entity Framework
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: d132583bba2520d37693be6c4b085cfa514003e0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737844"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient pro typy Entity Framework
Soubor manifestu poskytovatele .NET Framework Zprostředkovatel dat for SQL Server (SqlClient) obsahuje seznam primitivních typů poskytovatele, omezující vlastnosti pro každý typ, mapování mezi primitivními typy koncepčního modelu a modelu úložiště a povýšení a převod. pravidla mezi primitivními typy koncepčního a modelového modelu úložiště  
  
 Následující tabulka popisuje typy pro SQL Server 2008, SQL Server 2005 a SQL Server 2000 databáze a způsob mapování těchto typů na koncepční typy modelů. Některé nové typy byly představeny v novějších verzích SQL Server nejsou podporovány ve starších verzích nástroje SQL Server. Tyto typy jsou uvedeny v následující tabulce.  
  
|Typ poskytovatele<br /><br /> name|Typ poskytovatele<br /><br /> atributy|`EDMSimpleType`<br /><br /> name|Charakteristiky|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|není k dispozici|`Edm.Boolean`|není k dispozici|  
|`tinyint`|není k dispozici|`Edm.Byte`|není k dispozici|  
|`smallint`|není k dispozici|`Edm.Int16`|není k dispozici|  
|`int`|není k dispozici|`Edm.Int32`|není k dispozici|  
|`bigint`|není k dispozici|`Edm.Int64`|není k dispozici|  
|`float`|není k dispozici|`Edm.Double`|není k dispozici|  
|`real`|není k dispozici|`Edm.Double`|není k dispozici|  
|`decimal`|není k dispozici|`Edm.Decimal`|Číslic<br /><br /> -Minimum: 1<br /><br /> -Maximum: 38<br /><br /> – Výchozí: 18<br /><br /> -Constant: false<br /><br /> Kapacity<br /><br /> -Minimum: 0<br /><br /> -Maximum: 38<br /><br /> -Výchozí: 0<br /><br /> -Constant: false|  
|`numeric`|není k dispozici|`Edm.Decimal`|Číslic<br /><br /> -Minimum: 1<br /><br /> -Maximum: 38<br /><br /> – Výchozí: 18<br /><br /> -Constant: false<br /><br /> Kapacity<br /><br /> -Minimum: 0<br /><br /> -Maximum: 38<br /><br /> -Výchozí: 0<br /><br /> -Constant: false|  
|`smallmoney`|není k dispozici|`Edm.Decimal`|Číslic<br /><br /> – Výchozí: 10<br /><br /> -Constant: true<br /><br /> Kapacity<br /><br /> -Výchozí: 4<br /><br /> -Constant: true|  
|`money`|není k dispozici|`Edm.Decimal`|Číslic<br /><br /> – Výchozí: 19<br /><br /> -Constant: true<br /><br /> Kapacity<br /><br /> -Výchozí: 4<br /><br /> -Constant: true|  
|`binary`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maximum: 8000<br /><br /> -Výchozí: 8000<br /><br /> -Constant: false<br /><br /> FixedLength:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true|  
|`varbinary`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maximum: 8000<br /><br /> -Výchozí: 8000<br /><br /> -Constant: false<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`varbinary(max)`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2000.|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> -Výchozí: 214748364780<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`image`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> -Výchozí: 2147483647<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`timestamp`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> – Výchozí: 8<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true|  
|`rowversion`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> – Výchozí: 8<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true|  
|`smalldatetime`|není k dispozici|`Edm.DateTime`|Číslic<br /><br /> -Výchozí: 0<br /><br /> -Constant: true|  
|`datetime`|není k dispozici|`Edm.DateTime`|Číslic<br /><br /> – Výchozí: 3<br /><br /> -Constant: true|  
|`date`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTime`|Číslic<br /><br /> -Výchozí: 0<br /><br /> -Constant: false|  
|`time`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.Time`|Číslic<br /><br /> – Výchozí: 7<br /><br /> -Constant: false|  
|`datetime2`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTime`|Číslic<br /><br /> – Výchozí: 7<br /><br /> -Constant: false|  
|`datetimeoffset`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTimeOffset`|Číslic<br /><br /> – Výchozí: 7<br /><br /> -Constant: false|  
|`nvarchar`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2000.|není k dispozici|`Edm.String`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maximum: 4000<br /><br /> -Výchozí: 4000<br /><br /> -Constant: false<br /><br /> Unicode:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`varchar`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2000.|není k dispozici|`Edm.String`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maximum: 8000<br /><br /> -Výchozí: 8000<br /><br /> -Constant: false<br /><br /> Unicode:<br /><br /> -Výchozí: false<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`char`|není k dispozici|`Edm.String`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maximum: 8000<br /><br /> -Výchozí: 8000<br /><br /> -Constant: false<br /><br /> Unicode:<br /><br /> -Výchozí: false<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true|  
|`nchar`|není k dispozici|`Edm.String`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maximum: 4000<br /><br /> -Výchozí: 4000<br /><br /> -Constant: false<br /><br /> Unicode:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true|  
|`varchar`(`max`)|není k dispozici|`Edm.String`|MaxLength<br /><br /> -Výchozí: 2147483647<br /><br /> -Constant: true<br /><br /> Unicode:<br /><br /> -Výchozí: false<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`nvarchar`(`max`)|není k dispozici|`Edm.String`|MaxLength<br /><br /> -Výchozí: 1073741823<br /><br /> -Constant: true<br /><br /> Unicode:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`ntext`|Rovná se porovnatelný: false<br /><br /> Porovnatelné objednávky: false|`Edm.String`|MaxLength<br /><br /> -Výchozí: 1073741823<br /><br /> -Constant: true<br /><br /> Unicode:<br /><br /> -Výchozí: false<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`text`|Rovná se porovnatelný: false<br /><br /> Porovnatelné objednávky: false|`Edm.String`|MaxLength<br /><br /> -Výchozí: 2147483647<br /><br /> -Constant: true<br /><br /> Unicode:<br /><br /> -Výchozí: false<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
|`Unique`<br /><br /> `identifier`|Rovná se porovnatelný: true<br /><br /> Porovnat pořadí: pravda|`Edm.Guid`|není k dispozici|  
|`xml`|Rovná se porovnatelný: false<br /><br /> Porovnatelné objednávky: false|`Edm.String`|MaxLength<br /><br /> -Výchozí: 1073741823<br /><br /> -Constant: true<br /><br /> Unicode:<br /><br /> -Výchozí hodnota: true<br /><br /> -Constant: true<br /><br /> FixedLength:<br /><br /> -Výchozí: false<br /><br /> -Constant: true|  
  
## <a name="see-also"></a>Viz také:

- [Specifikace CSDL, SSDL a MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
