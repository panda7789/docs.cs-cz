---
title: Literály (entita SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 90c065dff0f81a743cd66e224885de01f6129b56
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767320"
---
# <a name="literals-entity-sql"></a>Literály (entita SQL)
Toto téma popisuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporu pro literály.  
  
## <a name="null"></a>Null  
 Literál null se používá k reprezentování hodnota null pro libovolného typu. Literál null je kompatibilní s žádným typem.  
  
 Hodnotou Null lze vytvořit pomocí přetypování prostřednictvím literálu s hodnotou null. Další informace najdete v tématu [PŘETYPOVÁNÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).  
  
 Pro pravidla o tom, kde volné plovoucí null literály lze použít, najdete v části [Null literály a odvození typu](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boolean  
 Logická hodnota literály jsou reprezentované pomocí klíčová slova `true` a `false`.  
  
## <a name="integer"></a>Integer  
 Můžou být celé číslo literály typu <xref:System.Int32> nebo <xref:System.Int64>. <xref:System.Int32> Literálu je řada číselné znaky. <xref:System.Int64> Literálu je řadu znaky následované velká L.  
  
## <a name="decimal"></a>Desetinné číslo  
 Číslo s pevnou desetinnou čárkou (decimální) je řadu číselné znaky, tečky (.) a další řadu znaky následované velká písmena "M".  
  
## <a name="float-double"></a>Float Double  
 Číslo s plovoucí desetinnou Dvojitá přesnost je řada číselné znaky, tečky (.) a další řadu znaky pravděpodobně následuje exponentem. Single přesnosti plovoucí číslo (nebo float) je Dvojitá přesnost plovoucí desetinnou čárkou bodu číslo syntaxe následuje f malá písmena.  
  
## <a name="string"></a>String  
 Řetězec je posloupnost znaků uzavřít do uvozovek nahoře. Uvozovky může být buď oba single uvozovky (`'`) nebo obě dvojité uvozovky ("). Textové literály znak může být ve formátu Unicode nebo kódování Unicode. Deklarovat řetězec znaků literálu jako Unicode, předpony literál s velká písmena "N". Výchozí hodnota je kódování Unicode znak textové literály. Může být žádné mezery mezi z N a řetězcovém literálu a z N musí být velkými písmeny.  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DateTime  
 Hodnota literálu datetime je nezávislý na národní prostředí a se skládá z část data a času část. Datum a čas části jsou povinné a neexistují žádné výchozí hodnoty.  
  
 Část data musí mít formát: `YYYY` - `MM` - `DD`, kde `YYYY` je hodnota čtyřmístné roku rozsahu 0001 až 9999, `MM` je od 1 do 12 měsíce a `DD` je den hodnotu, která je platná pro daný měsíc `MM`.  
  
 Časovou část musí mít formát: `HH`:`MM`[:`SS`[.fffffff]], kde `HH` je hodinu hodnota mezi 0 a 23, `MM` je minut hodnota mezi 0 a 59, `SS` je druhá hodnota mezi 0 a 59 a fffffff je zlomkové druhá hodnota mezi 0 a 9999999 tak. Všechny hodnoty rozsahy jsou inkluzivní. Zlomky sekund jsou volitelné. Sekund jsou volitelné, pokud jsou zadány zlomků sekund; v takovém případě se vyžadují sekund. Pokud nejsou zadané sekund nebo zlomků sekund, použije se místo toho výchozí hodnota nula.  
  
 Může existovat libovolný počet mezery mezi symbol data a času a literálu datové části, ale žádné nové řádky.  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Čas  
 Časový literál je nezávislé na národní prostředí a složený z jenom část času. Časovou část je povinná a neexistuje žádná výchozí hodnota. Musí mít ve formátu hh: mm [: SS [.fffffff]], kde HH je hodina hodnotu mezi 0 a 23, MM je minut hodnotu mezi 0 a 59, SS je druhá hodnota mezi 0 a 59 a fffffff je druhý podílem hodnotu mezi 0 a 9999999 tak. Všechny hodnoty rozsahy jsou inkluzivní. Zlomky sekund jsou volitelné. Sekund jsou volitelné, pokud jsou zadány zlomků sekund; v takovém případě se vyžadují sekund. Při sekund nebo zlomků nejsou zadané, použije se místo toho výchozí hodnota nula.  
  
 Může existovat libovolný počet mezery mezi symbol čas a literálu datové části, ale žádné nové řádky.  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 Datetimeoffset literálu je nezávislé na národní prostředí a složený z část data, času součástí a posunutí část. Datum, čas a posunutí částí, které jsou povinné a neexistují žádné výchozí hodnoty. Datum část musí mít formát rrrr-MM-DD, kde je rrrr hodnotu roku čtyřmístné rozsahu 0001 až 9999, MM je od 1 do 12 měsíce a DD den hodnotu, která je platná pro daný měsíc. Časovou část musí mít formát hh: mm [: SS [.fffffff]], kde HH jsou hodiny hodnota mezi 0 a 23, MM je minut hodnotu mezi 0 a 59, SS je druhá hodnota mezi 0 a 59 a fffffff je zlomkové druhá hodnota mezi 0 a 9999999 tak. Všechny hodnoty rozsahy jsou inkluzivní. Zlomky sekund jsou volitelné. Sekund jsou volitelné, pokud jsou zadány zlomků sekund; v takovém případě se vyžadují sekund. Při sekund nebo zlomků nejsou zadané, použije se místo toho výchozí hodnota nula. Posunutí část musí mít formát {+&#124;-} hh: mm, kde HH a MM mají stejný význam jako část času. Rozsah posun, ale musí být mezi-14: 00 a + 14:00  
  
 Může existovat libovolný počet mezery mezi DATETIMEOFFSET symbol a literálu datové části, ale žádné nové řádky.  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  Platná hodnota literálu Entity SQL můžete spadal mimo podporované oblasti pro CLR nebo zdroj dat. To může mít za následek výjimku  
  
## <a name="binary"></a>binární  
 Binární řetězcový literál je sekvenci hexadecimálních číslic jednoduchých uvozovek a být následující klíčové slovo binární nebo symbol zástupce `X` nebo `x`. Symbol zástupce `X` malá a velká písmena. Počtu nula či více mezery mezi klíčové slovo `binary` a hodnota binárního řetězce.  
  
 Hexadecimální znaky jsou také malá a velká písmena. Pokud je literál se skládá z lichý počet šestnáctkových číslic, literálové bude zarovnání na další i šestnáctková číslice pomocí prefixu literál s hexadecimální nulový počet číslic. Neexistuje žádné formální omezení velikosti binárního řetězce.  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Identifikátor GUID  
 A `GUID` literál představuje globálně jedinečný identifikátor. Je posloupnost vytvořen tak klíčové slovo `GUID` následuje šestnáctkových číslic ve formátu známé jako *registru* formátu: 8-4-4-4-12 uzavřená do jednoduchých uvozovek. Hexadecimální číslice jsou malá a velká písmena.  
  
 Může existovat libovolný počet mezery mezi GUID symbol a literálu datové části, ale žádné nové řádky.  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
