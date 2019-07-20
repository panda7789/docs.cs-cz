---
title: Připojovací řetězce v ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 02fe8d984f1287673477bb142b3f9626e248898e
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363746"
---
# <a name="connection-strings-in-adonet"></a>Připojovací řetězce v ADO.NET

Připojovací řetězec obsahuje inicializační informace, které jsou předány jako parametr od poskytovatele dat ke zdroji dat. Zprostředkovatel dat přijímá připojovací řetězec jako hodnotu <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> vlastnosti. Zprostředkovatel analyzuje připojovací řetězec a ověří, zda je syntaxe správná a zda jsou klíčová slova podporována. <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> Pak metoda předá analyzovaným parametrům připojení ke zdroji dat. Zdroj dat provádí další ověření a naváže připojení.

## <a name="connection-string-syntax"></a>Syntaxe připojovacího řetězce

Připojovací řetězec je seznam dvojic parametrů klíč/hodnota oddělených středníkem:

```
keyword1=value; keyword2=value;
```

V klíčových slovech se nerozlišují malá a velká písmena. V závislosti na zdroji dat ale můžou v nich být rozlišována velká a malá písmena. Klíčová slova a hodnoty mohou obsahovat [prázdné znaky](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Úvodní a koncové prázdné znaky jsou ignorovány v klíčových slovech a hodnotách v uvozovkách.

Pokud hodnota obsahuje středník, [řídicí znaky sady Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)nebo úvodní nebo koncové prázdné znaky, musí být uzavřeny v jednoduchých nebo dvojitých uvozovkách. Příklad:

```
Keyword=" whitespace  ";
Keyword='special;character';
```

Ohraničující znak se nesmí nacházet v rámci hodnoty, kterou obklopuje. Proto lze hodnotu obsahující jednoduché uvozovky uzavřít pouze do dvojitých uvozovek a naopak:

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

Ohraničující znak můžete také vložit pomocí dvou z nich dohromady:

```
Keyword="double""quotation";
Keyword='single''quotation';
```

Citace samotné a stejně jako znaménko rovná se nevyžadují uvozovací znaky, takže jsou platné následující připojovací řetězce:

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

Vzhledem k tomu, že každá hodnota je čtena do následujícího středníku nebo konce řetězce, hodnota v druhém příkladu `a=b=c`je a poslední středník je nepovinný.

Všechny připojovací řetězce sdílejí stejnou základní syntaxi popsanou výše. Sada rozpoznaných klíčových slov závisí na poskytovateli, ale na těchto letech se vyvinula z dřívějších rozhraní API, jako je například *ODBC*. Zprostředkovatel dat *.NET Framework* pro *SQL Server* (`SqlClient`) podporuje mnoho klíčových slov ze starších rozhraní API, ale je obecně flexibilnější a přijímá synonyma pro mnoho běžných klíčových slov řetězce připojení.

Psaní chyb může způsobit chyby. Například `Integrated Security=true` je platný, ale `IntegratedSecurity=true` způsobí chybu.

Připojovací řetězce konstruované ručně v době spuštění z neověřeného vstupu uživatele jsou zranitelné vůči útokům prostřednictvím injektáže řetězce a ohrožení zabezpečení ve zdroji dat. Pro řešení těchto problémů zavedlo *ADO.NET* 2,0 [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md) pro každého poskytovatele dat *.NET Framework* . Tyto tvůrci připojovacích řetězců zpřístupňují parametry jako vlastnosti silného typu a umožňují ověření připojovacího řetězce před jeho odesláním do zdroje dat.

## <a name="in-this-section"></a>V tomto oddílu

[Tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md)\
Ukazuje, jak použít `ConnectionStringBuilder` třídy pro vytvoření platných připojovacích řetězců za běhu.

[Připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\
Ukazuje, jak ukládat a načítat připojovací řetězce v konfiguračních souborech.

[Syntaxe připojovacího řetězce](../../../../docs/framework/data/adonet/connection-string-syntax.md)\
Popisuje postup konfigurace připojovacích řetězců specifických pro konkrétní poskytovatele `SqlClient`pro `OracleClient`, `OleDb`, a `Odbc`.

[Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)\
Ukazuje techniky ochrany informací používaných pro připojení ke zdroji dat.

## <a name="see-also"></a>Viz také:

- [Připojení ke zdroji dat](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
