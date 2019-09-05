---
title: SqlClient pro typy Entity Framework
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: af3a4eea08dd3f4e1a134fcb66d92bc4a3b077c7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248384"
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
|`decimal`|není k dispozici|`Edm.Decimal`|Číslic<br /><br /> Minimálně 1<br /><br /> Velikosti 38<br /><br /> Výchozí 18<br /><br /> Změnil False<br /><br /> Kapacity<br /><br /> Minimálně 0<br /><br /> Velikosti 38<br /><br /> Výchozí 0<br /><br /> Změnil False|  
|`numeric`|není k dispozici|`Edm.Decimal`|Číslic<br /><br /> Minimálně 1<br /><br /> Velikosti 38<br /><br /> Výchozí 18<br /><br /> Změnil False<br /><br /> Kapacity<br /><br /> Minimálně 0<br /><br /> Velikosti 38<br /><br /> Výchozí 0<br /><br /> Změnil False|  
|`smallmoney`|není k dispozici|`Edm.Decimal`|Číslic<br /><br /> Výchozí 10<br /><br /> Změnil Pravda<br /><br /> Kapacity<br /><br /> Výchozí 4<br /><br /> Změnil Pravda|  
|`money`|není k dispozici|`Edm.Decimal`|Číslic<br /><br /> Výchozí 19<br /><br /> Změnil Pravda<br /><br /> Kapacity<br /><br /> Výchozí 4<br /><br /> Změnil Pravda|  
|`binary`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> Minimálně 1<br /><br /> Velikosti 8000<br /><br /> Výchozí 8000<br /><br /> Změnil False<br /><br /> FixedLength:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda|  
|`varbinary`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> Minimálně 1<br /><br /> Velikosti 8000<br /><br /> Výchozí 8000<br /><br /> Změnil False<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`varbinary(max)`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2000.|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> Výchozí 214748364780<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`image`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> Výchozí 2147483647<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`timestamp`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> Výchozí 8<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda|  
|`rowversion`|není k dispozici|`Edm.Binary`|MaxLength<br /><br /> Výchozí 8<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda|  
|`smalldatetime`|není k dispozici|`Edm.DateTime`|Číslic<br /><br /> Výchozí 0<br /><br /> Změnil Pravda|  
|`datetime`|není k dispozici|`Edm.DateTime`|Číslic<br /><br /> Výchozí 3<br /><br /> Změnil Pravda|  
|`date`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTime`|Číslic<br /><br /> Výchozí 0<br /><br /> Změnil False|  
|`time`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.Time`|Číslic<br /><br /> Výchozí 7<br /><br /> Změnil False|  
|`datetime2`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTime`|Číslic<br /><br /> Výchozí 7<br /><br /> Změnil False|  
|`datetimeoffset`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2005 a SQL Server 2000.|není k dispozici|`Edm.DateTimeOffset`|Číslic<br /><br /> Výchozí 7<br /><br /> Změnil False|  
|`nvarchar`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2000.|není k dispozici|`Edm.String`|MaxLength<br /><br /> Minimálně 1<br /><br /> Velikosti 4000<br /><br /> Výchozí 4000<br /><br /> Změnil False<br /><br /> Unicode:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`varchar`<br /><br /> Poznámka: Tento typ není podporován v SQL Server 2000.|není k dispozici|`Edm.String`|MaxLength<br /><br /> Minimálně 1<br /><br /> Velikosti 8000<br /><br /> Výchozí 8000<br /><br /> Změnil False<br /><br /> Unicode:<br /><br /> Výchozí False<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`char`|není k dispozici|`Edm.String`|MaxLength<br /><br /> Minimálně 1<br /><br /> Velikosti 8000<br /><br /> Výchozí 8000<br /><br /> Změnil False<br /><br /> Unicode:<br /><br /> Výchozí False<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda|  
|`nchar`|není k dispozici|`Edm.String`|MaxLength<br /><br /> Minimálně 1<br /><br /> Velikosti 4000<br /><br /> Výchozí 4000<br /><br /> Změnil False<br /><br /> Unicode:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda|  
|`varchar`(`max`)|není k dispozici|`Edm.String`|MaxLength<br /><br /> Výchozí 2147483647<br /><br /> Změnil Pravda<br /><br /> Unicode:<br /><br /> Výchozí False<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`nvarchar`(`max`)|není k dispozici|`Edm.String`|MaxLength<br /><br /> Výchozí 1073741823<br /><br /> Změnil Pravda<br /><br /> Unicode:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`ntext`|Stejné srovnatelné: False<br /><br /> Porovnat pořadí: False|`Edm.String`|MaxLength<br /><br /> Výchozí 1073741823<br /><br /> Změnil Pravda<br /><br /> Unicode:<br /><br /> Výchozí False<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`text`|Stejné srovnatelné: False<br /><br /> Porovnat pořadí: False|`Edm.String`|MaxLength<br /><br /> Výchozí 2147483647<br /><br /> Změnil Pravda<br /><br /> Unicode:<br /><br /> Výchozí False<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
|`Unique`<br /><br /> `identifier`|Stejné srovnatelné: Pravda<br /><br /> Porovnat pořadí: Pravda|`Edm.Guid`|není k dispozici|  
|`xml`|Stejné srovnatelné: False<br /><br /> Porovnat pořadí: False|`Edm.String`|MaxLength<br /><br /> Výchozí 1073741823<br /><br /> Změnil Pravda<br /><br /> Unicode:<br /><br /> Výchozí Pravda<br /><br /> Změnil Pravda<br /><br /> FixedLength:<br /><br /> Výchozí False<br /><br /> Změnil Pravda|  
  
## <a name="see-also"></a>Viz také:

- [Specifikace CSDL, SSDL a MSL](./language-reference/csdl-ssdl-and-msl-specifications.md)
