---
title: Připojovací řetězce v ADO.NET
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: b4e057cab4c562fc51893631c35d66409e1c3731
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006116"
---
# <a name="connection-strings-in-adonet"></a>Připojovací řetězce v ADO.NET
Rozhraní .NET Framework 2.0 zavedeny nové funkce pro práci s řetězci připojení, včetně představení nových klíčových slov na tvůrce třídy řetězec připojení, které usnadňují vytváření platný připojovací řetězce v době běhu.  
  
 Připojovací řetězec obsahuje informace o inicializaci, která je předána jako parametr od poskytovatele dat ke zdroji dat. Syntaxe závisí na poskytovateli dat a připojovací řetězec je analyzován při pokusu o otevření připojení. Chyby syntaxe vygenerovat výjimku za běhu, ale až po informace o připojení obdrží zdroj dat dojít k jiným chybám. Jakmile ověříte, zdroj dat platí volby zadané v připojovacím řetězci a otevře připojení.  
  
 Formát připojovacího řetězce je středníkem oddělený seznam dvojic klíč/hodnota parametru:  
  
 `keyword1=value; keyword2=value;`  
  
 Klíčová slova nejsou velká a malá písmena a mezery mezi páry klíč/hodnota jsou ignorovány. Hodnoty mohou být velká a malá písmena, v závislosti na zdroji dat. Všechny hodnoty obsahující středník, jednoduchých uvozovek nebo dvojité uvozovky musí být uzavřena v dvojitých uvozovkách.  
  
 Platný připojovací řetězec syntaxe závisí na poskytovateli a v průběhu let ze starší rozhraní API, jako je rozhraní ODBC se vyvinula. Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) zahrnuje mnoho prvků ze starší syntaxi a je obecně flexibilnější s běžné syntaxe připojovacího řetězce. Jsou často stejně platná synonyma pro elementy syntaxe připojovacího řetězce, ale některé syntaxe a pravopisné chyby může způsobit problémy. Například "`Integrated Security=true`" platí, že "`IntegratedSecurity=true`" způsobí chybu. Kromě toho připojovací řetězce vytvořeným za běhu z neověřený vstup uživatele může vést k útokům prostřednictvím injektáže řetězec, ohrožující zabezpečení ve zdroji dat.  
  
 K řešení těchto problémů, ADO.NET 2.0 zavedeny nové tvůrci připojovacích řetězců pro každého poskytovatele dat .NET Framework. Klíčová slova jsou vystaveny jako vlastnosti, povolení syntaxe připojovacího řetězce k ověření před odesláním do zdroje dat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Popisuje způsob použití `ConnectionStringBuilder` třídy sestavit platný připojovací řetězce v běhu.  
  
 [Připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Ukazuje, jak k ukládání a načítání připojovacích řetězců v konfiguračních souborech.  
  
 [Syntaxe připojovacího řetězce](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 Popisuje postup konfigurace specifickým pro zprostředkovatele připojovací řetězce pro `SqlClient`, `OracleClient`, `OleDb`, a `Odbc`.  
  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Ukazuje postupy ochrany osobních údajů pro připojení ke zdroji dat.  
  
## <a name="see-also"></a>Viz také  
 [Připojení ke zdroji dat](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
