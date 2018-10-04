---
title: Připojovací řetězce v ADO.NET
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 1e6e2b6870195c99279639e1f4576a30b7126d4d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583684"
---
# <a name="connection-strings-in-adonet"></a>Připojovací řetězce v ADO.NET
Rozhraní .NET Framework 2.0 zavedeny nové funkce pro práci s řetězci připojení, včetně představení nových klíčových slov na tvůrce třídy řetězec připojení, které usnadňují vytváření platný připojovací řetězce v době běhu.  
  
Připojovací řetězec obsahuje informace o inicializaci, která je předána jako parametr od poskytovatele dat ke zdroji dat. Syntaxe závisí na poskytovateli dat a připojovací řetězec je analyzován při pokusu o otevření připojení. Chyby syntaxe vygenerovat výjimku za běhu, ale až po informace o připojení obdrží zdroj dat dojít k jiným chybám. Jakmile ověříte, zdroj dat platí volby zadané v připojovacím řetězci a otevře připojení.
  
Formát připojovacího řetězce je středníkem oddělený seznam dvojic klíč/hodnota parametru:
  
    keyword1=value; keyword2=value;
  
Klíčová slova nerozlišují malá a velká písmena. Hodnoty, ale mohou být velká a malá písmena, v závislosti na zdroji dat. Klíčová slova a hodnoty mohou obsahovat [prázdné znaky](https://en.wikipedia.org/wiki/Whitespace_character#Unicode), i když úvodní a koncové mezery bude ignorován v klíčových slov a nekotované hodnoty.

Obsahuje-li hodnota středník, [řídící znaky Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters), úvodní a koncové prázdné znaky musí být uzavřen v jednoduchých nebo dvojitých uvozovek, například:

    Keyword=" whitespace  ";
    Keyword='special;character';

Nadřazené znak nedojde v rámci hodnoty, který ji obklopuje. Proto můžou být uzavřená hodnotu obsahující jednoduchých uvozovek pouze dvojité uvozovky a naopak:

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

Uvozovky sami, stejně jako znaménko rovná se nevyžadují, aby uvozovací znaky, takže následující připojovací řetězce jsou platné:

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

Protože každá hodnota je pro čtení do další středníkem nebo konec řetězce, je hodnota v druhém příkladu `a=b=c`, a poslední středník je volitelné.

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
