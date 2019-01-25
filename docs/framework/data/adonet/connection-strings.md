---
title: Připojovací řetězce v ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: c765eee661858499240344cb5059fe1fa9a58ab5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627561"
---
# <a name="connection-strings-in-adonet"></a>Připojovací řetězce v ADO.NET

Připojovací řetězec obsahuje informace o inicializaci, která je předána jako parametr od poskytovatele dat ke zdroji dat. Zprostředkovatel dat přijímá jako hodnotu připojovacího řetězce <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> vlastnost. Zprostředkovatel analyzuje připojovací řetězec a zajistí, že je syntaxe správná a že jsou podporované klíčová slova. Pak bude <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> metoda předává parametry analyzovaný připojení ke zdroji dat. Zdroj dat provádí další ověřování a naváže připojení.

## <a name="connection-string-syntax"></a>Syntaxe připojovacího řetězce

Připojovací řetězec se středníkem oddělený seznam dvojic klíč/hodnota parametru:
  
    keyword1=value; keyword2=value;
  
Klíčová slova nerozlišují malá a velká písmena. Hodnoty, ale mohou být velká a malá písmena, v závislosti na zdroji dat. Klíčová slova a hodnoty mohou obsahovat [prázdné znaky](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Počáteční a koncové mezery bude ignorován v klíčových slov a nekotované hodnoty.

Obsahuje-li hodnota středník, [řídící znaky Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters), nebo úvodní a koncové prázdné znaky, musí být uzavřen v jednoduchých nebo dvojitých uvozovek. Příklad:

    Keyword=" whitespace  ";
    Keyword='special;character';

Nadřazené znak nedojde v rámci hodnoty, který ji obklopuje. Proto můžou být uzavřená hodnotu obsahující jednoduchých uvozovek pouze do dvojitých uvozovek a naopak:

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

Uvozovky sami, stejně jako znaménko rovná se nevyžadují, aby uvozovací znaky, takže následující připojovací řetězce jsou platné:

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

Protože každá hodnota je pro čtení do další středníkem nebo konec řetězce, je hodnota v druhém příkladu `a=b=c`, a poslední středník je volitelné.

Všechny řetězce připojení sdílet stejnou základní syntaxi popsané výše. Sada rozpoznaný klíčová slova závisí na poskytovateli, ale a průběžně vyvíjel let ze starší rozhraní API, jako *ODBC*. *Rozhraní .NET Framework* zprostředkovatel dat pro *systému SQL Server* (`SqlClient`) podporuje mnoho klíčových slov z starší rozhraní API, ale je obecně flexibilnější a přijímá synonyma pro spoustu běžných připojovací řetězec klíčová slova.

Překlepů mohou způsobit chyby. Například `Integrated Security=true` je platný, ale `IntegratedSecurity=true` způsobí chybu.

Připojovací řetězce s ručně vytvořeným za běhu z neověřený vstup uživatele je ohrožen útoky prostřednictvím injektáže řetězec a by mohly ohrozit zabezpečení ve zdroji dat. K řešení těchto problémů *ADO.NET* 2.0 zavedl [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md) pro každou *rozhraní .NET Framework* poskytovatele dat služeb. Tyto tvůrci připojovacích řetězců vystavit parametry jako vlastnosti silného typu a bude možné ověřit připojovací řetězec před odesláním do zdroje dat.

## <a name="in-this-section"></a>V tomto oddílu  
 [Tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Popisuje způsob použití `ConnectionStringBuilder` třídy sestavit platný připojovací řetězce v běhu.
  
 [Připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Ukazuje, jak k ukládání a načítání připojovacích řetězců v konfiguračních souborech.
  
 [Syntaxe připojovacího řetězce](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 Popisuje postup konfigurace specifickým pro zprostředkovatele připojovací řetězce pro `SqlClient`, `OracleClient`, `OleDb`, a `Odbc`.
  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Ukazuje postupy ochrany osobních údajů pro připojení ke zdroji dat.
  
## <a name="see-also"></a>Viz také:
- [Připojení ke zdroji dat](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
