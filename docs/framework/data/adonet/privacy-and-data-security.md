---
title: "Ochrana osobních údajů a zabezpečení dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 87b83732f1a34db848733c658f35f151c4de4e39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="privacy-and-data-security"></a>Ochrana osobních údajů a zabezpečení dat
Zabezpečení a správa citlivých informací v aplikaci ADO.NET je závislé na základní produkty a technologie použitá k jeho vytvoření. ADO.NET přímo neposkytuje služby pro zabezpečení nebo šifrovat data.  
  
## <a name="cryptography-and-hash-codes"></a>Šifrování a kódů Hash  
 Třídy v rozhraní .NET Framework <xref:System.Security.Cryptography> oboru názvů lze ze svých aplikací ADO.NET zamezí dat se přečíst nebo upravit neoprávněným třetím stranám. Některé třídy jsou obálek pro nespravované Microsoft CryptoAPI, zatímco jiné jsou spravované implementace. [Šifrovacím službám](http://msdn.microsoft.com/en-us/68a1e844-c63c-44af-9247-f6716eb23781) téma obsahuje přehled kryptografie v rozhraní .NET Framework, popisuje, jak je implementována cryptograph a jak můžete provádět konkrétní kryptografické úlohy.  
  
 Na rozdíl od kryptografie, která umožňuje šifrované a pak dešifrování dat, data algoritmu hash je jednosměrný proces. Použití algoritmu hash dat je užitečné, když chcete zabránit manipulaci kontrolou, že data nikdo nezměnil: zadána identické vstupní řetězce délkami algoritmů hash vždy vytvořila identické krátký výstupní hodnoty, které lze snadno porovnat. [Zajištění Integrity dat pomocí hodnot hash](../../../../docs/standard/security/ensuring-data-integrity-with-hash-codes.md) popisuje, jak můžete vytvořit a ověřit hodnoty hash.  
  
## <a name="encrypting-configuration-files"></a>Šifrování konfiguračních souborů  
 Zabezpečení přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečení aplikace. Připojovací řetězec uvede potenciální ohrožení zabezpečení, pokud není zabezpečená. Připojovací řetězce, které jsou uloženy v konfiguračních souborech jsou uloženy v standardní soubory XML, pro které je rozhraní .NET Framework definovaný společnou sadu elementů. Chráněné konfigurace umožňuje šifrování citlivých informací v konfiguračním souboru. I když primárně určený pro aplikace ASP.NET, chráněné konfigurace mohou sloužit také k šifrování souboru konfigurační oddíly funkce v aplikace systému Windows. Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Zabezpečení řetězcové hodnoty v paměti  
 Pokud <xref:System.String> objekt obsahuje citlivé informace, jako jsou hesla, číslo platební karty a osobní data, existuje riziko, které by mohly být informace zjistí po se používá, protože aplikace nemůže odstranit data z paměti počítače.  
  
 A <xref:System.String> se nedá změnit; jeho hodnotu nelze změnit po vytvoření. Změny, které se zobrazují změnit hodnotu řetězce ve skutečnosti vytvořit novou instanci třídy <xref:System.String> objektu v paměti, ukládání dat jako prostý text. Kromě toho není možné k předpovědi řetězec instance budou odstraněny z paměti. Recyklace paměti s řetězci není deterministický s uvolňování paměti .NET. Neměli byste používat <xref:System.String> a <xref:System.Text.StringBuilder> třídy, pokud je skutečně citlivá data.  
  
 <xref:System.Security.SecureString> Třída poskytuje metody pro šifrování textu s použitím Data Protection API (DPAPI) v paměti. Řetězec je pak odstraněn z paměti, když už ho nepotřebují. Neexistuje žádné `ToString` metoda rychle číst obsah <xref:System.Security.SecureString>. Bude možné inicializovat novou instanci třídy `SecureString` se žádná hodnota nebo předání ukazatele na pole <xref:System.Char> objekty. Potom můžete různé metody třídy pro práci s řetězcem. Další informace, stáhněte si [SecureString ukázkovou aplikaci](http://go.microsoft.com/fwlink/?LinkId=120418), která demonstruje použití `SecureString` třídy z.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zabezpečení SQL serveru](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
