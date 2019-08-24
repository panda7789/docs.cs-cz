---
title: Ochrana osobních údajů a zabezpečení dat
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: e4f603d35b4fc03eff990570e725a9d063c19faa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69988725"
---
# <a name="privacy-and-data-security"></a>Ochrana osobních údajů a zabezpečení dat
Zabezpečení a Správa citlivých informací v aplikaci ADO.NET závisí na základních produktech a technologiích, které jste použili k jejímu vytvoření. ADO.NET přímo neposkytuje služby pro zabezpečení nebo šifrování dat.  
  
## <a name="cryptography-and-hash-codes"></a>Kryptografie a kódy hash  
 Třídy v oboru názvů .NET Framework <xref:System.Security.Cryptography> lze použít z aplikací ADO.NET k tomu, abyste zabránili čtení nebo úpravám dat neoprávněnými třetími stranami. Některé třídy jsou obálky pro nespravované rozhraní Microsoft CryptoAPI, zatímco jiné jsou spravované implementace. Téma [kryptografických služeb](../../../standard/security/cryptographic-services.md) poskytuje přehled kryptografie v .NET Framework, popisuje, jak je implementováno cryptograph a jak můžete provádět konkrétní kryptografické úlohy.  
  
 Na rozdíl od kryptografie, která umožňuje šifrování a pak dešifrování dat, je jednosměrnou metodou zpracování dat algoritmem hash. Data hash jsou užitečná, když chcete zabránit manipulaci tím, že zkontrolujete, že se data nezměnila: stejné vstupní řetězce, algoritmy hash vždy vytvoří identické krátké výstupní hodnoty, které lze snadno porovnat. [Zajištění integrity dat pomocí kódů hash](../../../standard/security/ensuring-data-integrity-with-hash-codes.md) popisuje, jak můžete generovat a ověřit hodnoty hash.  
  
## <a name="encrypting-configuration-files"></a>Šifrování konfiguračních souborů  
 Ochrana přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečení aplikace. Připojovací řetězec představuje potenciální chybu zabezpečení, pokud není zabezpečená. Připojovací řetězce uložené v konfiguračních souborech jsou uloženy ve standardních souborech XML, pro které .NET Framework definovaly společnou sadu prvků. Chráněná konfigurace umožňuje šifrovat citlivé informace v konfiguračním souboru. I když jsou primárně určené pro aplikace ASP.NET, chráněná konfigurace se dá použít taky k šifrování oddílů konfiguračního souboru v aplikacích pro Windows. Další informace najdete v tématu [ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Zabezpečení řetězcových hodnot v paměti  
 <xref:System.String> Pokud objekt obsahuje citlivé informace, jako je například heslo, číslo platební karty nebo osobní údaje, existuje riziko, že tyto informace mohou být po použití odhaleny, protože aplikace nemůže odstranit data z paměti počítače.  
  
 Objekt <xref:System.String> je neměnný. jeho hodnotu nelze po vytvoření změnit. Změny, které se zobrazí pro úpravu řetězcové hodnoty, ve skutečnosti vytvoří novou <xref:System.String> instanci objektu v paměti a uloží data jako prostý text. Kromě toho není možné předpovědět, kdy budou instance řetězců odstraněny z paměti. Recyklace paměti s řetězci není deterministické pro uvolňování paměti .NET. Nepoužívejte třídy <xref:System.Text.StringBuilder>a, Pokud jsou data skutečně citlivá. <xref:System.String>  
  
 <xref:System.Security.SecureString> Třída poskytuje metody pro šifrování textu pomocí data Protection API (DPAPI) v paměti. Řetězec se pak odstraní z paměti, když už nepotřebujete. Neexistuje žádná `ToString` metoda pro rychlé čtení obsahu <xref:System.Security.SecureString>. Můžete inicializovat novou instanci `SecureString` bez hodnoty nebo předáním ukazatele na <xref:System.Char> pole objektů. Pak můžete použít různé metody třídy pro práci s řetězcem. Chcete-li získat další informace, Stáhněte si [ukázkovou aplikaci SecureString](https://go.microsoft.com/fwlink/?LinkId=120418), která ukazuje `SecureString` , jak použít třídu z.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
