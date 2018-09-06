---
title: Čísla s plovoucí desetinnou čárkou
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: 2ab583a07c78cfa06ac597c369486f89e19ca66e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042348"
---
# <a name="floating-point-numbers"></a>Čísla s plovoucí desetinnou čárkou
Toto téma popisuje některé z problémů, které vývojáři často dojde při práci s čísly s plovoucí desetinnou čárkou v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Tyto jsou způsobené tím, že počítače ukládána čísla s plovoucí desetinnou čárkou a nejsou specifická pro konkrétního poskytovatele, jako <xref:System.Data.SqlClient> nebo <xref:System.Data.OracleClient>.  
  
 Čísla s plovoucí desetinnou čárkou obvykle nemají přesné binárního formátu. Místo toho počítače ukládá přibližný počet. V různou dobu může být různý počet číslic binární soubor používá k reprezentování číslo. Když plovoucí bodu, že číslo je převedeno z jednoho znázornění na jiné vyjádření nejmenších platných číslicích toto číslo může mírně lišit. Převod je obvykle dochází, když číslo přetypováno z jednoho typu na jiný typ. Změna vyvolá se, zda převod vyvolá se v rámci databáze, mezi typy, které představují hodnot v databázi nebo mezi typy. Z důvodů těchto změn může mít čísla, která by byla logicky stejné změny v jejich nejméně významných číslic, které způsobí tak, aby měly různé hodnoty. Počet číslic v číslo může být větší nebo menší, než se očekávalo. Když naformátovaná jako řetězec, číslo nemusí zobrazit očekávané hodnotě.  
  
 Pro minimalizaci negativních dopadů, měli byste použít nejvíce odpovídá mezi číselnými typy, které je k dispozici. Například pokud pracujete s SQL serverem, přesné číselná hodnota může změnit hodnotu příkazů jazyka Transact-SQL aplikace skutečný typ při převodu na hodnotu typu float. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], převod <xref:System.Single> k <xref:System.Double> může také vést k neočekávaným výsledkům. V obou těchto případech je dobrou strategii, aby všechny hodnoty v aplikace využívají stejné číselného typu. Můžete také použít typ desetinné číslo-přesnost nebo přetypovat na typ desetinné číslo-přesnost s plovoucí desetinnou čárkou čísla, než začnete pracovat s nimi.  
  
 Chcete-li vyřešit problémy s porovnání rovnosti, vezměte v úvahu kódování aplikace tak, aby se ignorují odchylky v nejmenších platných číslicích. Například namísto porovnání najdete v článku, zda jsou stejné dvě čísla, odečte jednu číslici od jiné číslo. Pokud rozdíl je v rámci přijatelných okraji zaokrouhlení, můžete aplikace řešte čísel jakoby se shodují.  
  
## <a name="see-also"></a>Viz také  
 [Proč čísla s plovoucí desetinnou čárkou můžou ztratit přesnost](https://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
