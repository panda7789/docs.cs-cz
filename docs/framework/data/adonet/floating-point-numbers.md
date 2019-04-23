---
title: Čísla s plovoucí desetinnou čárkou
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: aae7bd2ea6b5ba7bc9c69b99c93b62ba7a413d59
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102515"
---
# <a name="floating-point-numbers"></a>Čísla s plovoucí desetinnou čárkou
Toto téma popisuje některé z problémů, které vývojáři často dojde při práci s čísly s plovoucí desetinnou čárkou v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Tyto jsou způsobené tím, že počítače ukládána čísla s plovoucí desetinnou čárkou a nejsou specifická pro konkrétního poskytovatele, jako <xref:System.Data.SqlClient> nebo <xref:System.Data.OracleClient>.  
  
 Čísla s plovoucí desetinnou čárkou obvykle nemají přesné binárního formátu. Místo toho počítače ukládá přibližný počet. V různou dobu může být různý počet číslic binární soubor používá k reprezentování číslo. Když plovoucí bodu, že číslo je převedeno z jednoho znázornění na jiné vyjádření nejmenších platných číslicích toto číslo může mírně lišit. Převod je obvykle dochází, když číslo přetypováno z jednoho typu na jiný typ. Změna vyvolá se, zda převod vyvolá se v rámci databáze, mezi typy, které představují hodnot v databázi nebo mezi typy. Z důvodů těchto změn může mít čísla, která by byla logicky stejné změny v jejich nejméně významných číslic, které způsobí tak, aby měly různé hodnoty. Počet číslic v číslo může být větší nebo menší, než se očekávalo. Když naformátovaná jako řetězec, číslo nemusí zobrazit očekávané hodnotě.  
  
 Pro minimalizaci negativních dopadů, měli byste použít nejvíce odpovídá mezi číselnými typy, které je k dispozici. Například pokud pracujete s SQL serverem, přesné číselná hodnota může změnit hodnotu příkazů jazyka Transact-SQL aplikace skutečný typ při převodu na hodnotu typu float. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], převod <xref:System.Single> k <xref:System.Double> může také vést k neočekávaným výsledkům. V obou těchto případech je dobrou strategii, aby všechny hodnoty v aplikace využívají stejné číselného typu. Můžete také použít typ desetinné číslo-přesnost nebo přetypovat na typ desetinné číslo-přesnost s plovoucí desetinnou čárkou čísla, než začnete pracovat s nimi.  
  
 Chcete-li vyřešit problémy s porovnání rovnosti, vezměte v úvahu kódování aplikace tak, aby se ignorují odchylky v nejmenších platných číslicích. Například namísto porovnání najdete v článku, zda jsou stejné dvě čísla, odečte jednu číslici od jiné číslo. Pokud rozdíl je v rámci přijatelných okraji zaokrouhlení, můžete aplikace řešte čísel jakoby se shodují.  
  
## <a name="see-also"></a>Viz také:

- [Proč čísla s plovoucí desetinnou čárkou můžou ztratit přesnost](/cpp/build/reference/why-floating-point-numbers-may-lose-precision)
- [Přehled ADO.NET](ado-net-overview.md)
