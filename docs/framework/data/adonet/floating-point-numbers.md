---
title: Čísla s plovoucí desetinnou čárkou
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: 1f76a6ab8cc2a44580229014dd8ebae6b317921f
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374418"
---
# <a name="floating-point-numbers"></a>Čísla s plovoucí desetinnou čárkou
Toto téma popisuje některé problémy, se kterými se vývojáři často setkávají při práci s čísly s plovoucí desetinnou čárkou v ADO.NET. Tyto problémy způsobují způsob, jakým počítače ukládají čísla s plovoucí desetinnou čárkou a nejsou specifické pro konkrétního poskytovatele, jako <xref:System.Data.SqlClient> je <xref:System.Data.OracleClient>například nebo.  
  
 Čísla s plovoucí desetinnou čárkou většinou nemají přesnou binární reprezentaci. Místo toho počítač ukládá přibližné číslo. V různých časech lze použít různé číslice binárních číslic, které reprezentují číslo. Když je číslo s plovoucí desetinnou čárkou převedeno z jedné reprezentace na jiné reprezentace, nejnižší významné číslice tohoto čísla se mohou mírně lišit. K převodu obvykle dochází, když je číslo přetypování z jednoho typu na jiný typ. K této změně dochází, je-li převod v rámci databáze, mezi typy, které reprezentují hodnoty databáze nebo mezi typy. Z důvodu těchto změn mohou mít počty, které logicky mají stejnou hodnotu, pravděpodobně změny v jejich nejméně významných číslicích, což způsobí, že mají různé hodnoty. Počet číslic přesnosti v čísle může být větší nebo menší, než se očekávalo. Při formátování jako řetězce nesmí číslo zobrazovat očekávanou hodnotu.  
  
 K minimalizaci těchto efektů byste měli použít nejbližší shodu mezi číselnými typy, které jsou vám k dispozici. Například pokud pracujete se SQL Server, může se přesná číselná hodnota změnit, pokud převedete hodnotu Transact-SQL reálného typu na hodnotu typu float. V .NET Framework může převod typu <xref:System.Single> na a <xref:System.Double> také způsobit neočekávané výsledky. V obou těchto případech je dobré zajistit, aby všechny hodnoty v aplikaci používaly stejný číselný typ. Před tím, než s nimi budete pracovat, můžete také použít desítkový typ s pevnou přesností nebo přetypovat čísla s plovoucí desetinnou čárkou na typ desetinné číslo s pevnou přesností.  
  
 Chcete-li vyřešit problémy s porovnáním rovnosti, zvažte kódování aplikace tak, aby variace nejméně významných číslic byly ignorovány. Například místo porovnání, abyste viděli, zda jsou dvě čísla shodná, ododečte jedno číslo od druhého čísla. Je-li rozdíl v rámci přijatelného rozpětí zaokrouhlení, může aplikace zacházet s čísly, jako kdyby byly stejné.  
  
## <a name="see-also"></a>Viz také:

- [Proč čísla s plovoucí desetinnou čárkou můžou ztratit přesnost](/cpp/build/why-floating-point-numbers-may-lose-precision)
- [Přehled ADO.NET](ado-net-overview.md)
