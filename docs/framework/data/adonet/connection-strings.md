---
title: Připojovací řetězce
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: cb0b2831a22f3fe51dd7c5bfbe51e72f266a0003
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980233"
---
# <a name="connection-strings-in-adonet"></a>Připojovací řetězce v ADO.NET

Připojovací řetězec obsahuje inicializační informace, které jsou předány jako parametr od poskytovatele dat ke zdroji dat. Zprostředkovatel dat přijímá připojovací řetězec jako hodnotu vlastnosti <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>. Zprostředkovatel analyzuje připojovací řetězec a ověří, zda je syntaxe správná a zda jsou klíčová slova podporována. Poté metoda <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> předá parametry analyzovaného připojení ke zdroji dat. Zdroj dat provádí další ověření a naváže připojení.

## <a name="connection-string-syntax"></a>Syntaxe připojovacího řetězce

Připojovací řetězec je seznam dvojic parametrů klíč/hodnota oddělených středníkem:

```csharp
keyword1=value; keyword2=value;
```

V klíčových slovech se nerozlišují malá a velká písmena. V závislosti na zdroji dat ale můžou v nich být rozlišována velká a malá písmena. Klíčová slova a hodnoty mohou obsahovat [prázdné znaky](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Úvodní a koncové prázdné znaky jsou ignorovány v klíčových slovech a hodnotách v uvozovkách.

Pokud hodnota obsahuje středník, [řídicí znaky sady Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)nebo úvodní nebo koncové prázdné znaky, musí být uzavřeny v jednoduchých nebo dvojitých uvozovkách. Příklad:

```csharp
Keyword=" whitespace  ";
Keyword='special;character';
```

Ohraničující znak se nesmí nacházet v rámci hodnoty, kterou obklopuje. Proto lze hodnotu obsahující jednoduché uvozovky uzavřít pouze do dvojitých uvozovek a naopak:

```csharp
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

Ohraničující znak můžete také vložit pomocí dvou z nich dohromady:

```csharp
Keyword="double""quotation";
Keyword='single''quotation';
```

Citace samotné a stejně jako znaménko rovná se nevyžadují uvozovací znaky, takže jsou platné následující připojovací řetězce:

```csharp
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

Vzhledem k tomu, že každá hodnota je čtena do dalšího středníku nebo konce řetězce, hodnota v druhém příkladu je `a=b=c`a poslední středník je nepovinný.

Všechny připojovací řetězce sdílejí stejnou základní syntaxi popsanou výše. Sada rozpoznaných klíčových slov závisí na poskytovateli, ale na těchto letech se vyvinula z dřívějších rozhraní API, jako je například *ODBC*. Zprostředkovatel dat *.NET Framework* pro *SQL Server* (`SqlClient`) podporuje mnoho klíčových slov ze starších rozhraní API, ale je obecně flexibilnější a přijímá synonyma pro mnohé běžné klíčová slova připojovacího řetězce.

Psaní chyb může způsobit chyby. Například `Integrated Security=true` je platný, ale `IntegratedSecurity=true` způsobí chybu.

Připojovací řetězce konstruované ručně v době spuštění z neověřeného vstupu uživatele jsou zranitelné vůči útokům prostřednictvím injektáže řetězce a ohrožení zabezpečení ve zdroji dat. Pro řešení těchto problémů zavedlo *ADO.NET* 2,0 [tvůrci připojovacích řetězců](connection-string-builders.md) pro každého poskytovatele dat *.NET Framework* . Tyto tvůrci připojovacích řetězců zpřístupňují parametry jako vlastnosti silného typu a umožňují ověření připojovacího řetězce před jeho odesláním do zdroje dat.

## <a name="in-this-section"></a>V tomto oddílu

\ pro [sestavování připojovacích řetězců](connection-string-builders.md)
Ukazuje, jak použít třídy `ConnectionStringBuilder` k vytvoření platných připojovacích řetězců v době běhu.

[Připojovací řetězce a konfigurační soubory](connection-strings-and-configuration-files.md)\
Ukazuje, jak ukládat a načítat připojovací řetězce v konfiguračních souborech.

\ [syntaxe připojovacího řetězce](connection-string-syntax.md)
Popisuje postup konfigurace připojovacích řetězců specifických pro konkrétní poskytovatele pro `SqlClient`, `OracleClient`, `OleDb`a `Odbc`.

[Ochrana\ informací o připojení](protecting-connection-information.md)
Ukazuje techniky ochrany informací používaných pro připojení ke zdroji dat.

## <a name="see-also"></a>Viz také:

- [Připojení ke zdroji dat](/cpp/data/odbc/connecting-to-a-data-source)
- [Přehled ADO.NET](ado-net-overview.md)
