---
title: Literály (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: e07dd3217e133fff98beb11ecad47e1474e4974a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319667"
---
# <a name="literals-entity-sql"></a>Literály (Entity SQL)
Toto téma popisuje podporu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pro literály.  
  
## <a name="null"></a>Null  
 Literál null se používá k reprezentaci hodnoty null pro libovolný typ. Literál s hodnotou null je kompatibilní s jakýmkoli typem.  
  
 Typové hodnoty null lze vytvořit přetypováním přes literál s hodnotou null. Další informace najdete v tématu [přetypování](cast-entity-sql.md).  
  
 Pravidla o tom, kde lze použít bezplatné plovoucí literály null, naleznete v tématu [literály s hodnotou null a odvození typu](null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boolean  
 Logické literály jsou reprezentovány klíčovými slovy `true` a `false`.  
  
## <a name="integer"></a>Integer  
 Celočíselné literály mohou být typu <xref:System.Int32> nebo <xref:System.Int64>. Literál <xref:System.Int32> je řada číselných znaků. Literál <xref:System.Int64> je série číselných znaků následovaných velkým L.  
  
## <a name="decimal"></a>Desetinné číslo  
 Číslo s pevnou desetinnou čárkou (desítkově) je série číselných znaků, tečka (.) a další řada číselných znaků následovaných velkým písmenem "M".  
  
## <a name="float-double"></a>Float, Double  
 Číslo s plovoucí desetinnou čárkou a dvojitou přesností je řada číselných znaků, tečka (.) a další řada číselných znaků, které jsou pravděpodobně následovány exponentem. Číslo s plovoucí desetinnou čárkou s jednoduchou přesností (neboli float) je syntaxe čísla s plovoucí desetinnou čárkou s dvojitou přesností následovaný malým písmenem f.  
  
## <a name="string"></a>String  
 Řetězec je řada znaků uzavřených v uvozovkách. Uvozovky mohou být buď jednoduché (`'`), nebo obě dvojité uvozovky ("). Řetězcové literály znaků můžou být Unicode nebo jiné než Unicode. Chcete-li deklarovat řetězcový literál znaků jako Unicode, zaprefixujte literál s velkým písmenem "N". Výchozí hodnoty jsou řetězcové literály, které nejsou znakové sady Unicode. Mezi N a datovou částí literálu řetězce nemůže být žádná mezera a N musí být velká.  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DateTime  
 Literál DateTime je nezávislý na národním prostředí a skládá se z části data a času. Části data a času jsou povinné a nejsou k dispozici žádné výchozí hodnoty.  
  
 Část data musí mít formát: `YYYY` @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4, kde `YYYY` je hodnota roku v 9999 rozmezí 1 až 12 až `DD` @no__t, což je hodnota dne platná pro daný měsíc `MM`.  
  
 Časový interval musí mít formát: `HH`: `MM` [: `SS` [. fffffff]], kde `HH` je hodnota hodiny mezi 0 a 23, `MM` je minutová hodnota mezi 0 a 59, `SS` je druhá hodnota mezi 0 a 59 a fffffff je desetinná sekundová hodnota. mezi 0 a 9999999. Všechny rozsahy hodnot jsou včetně. Zlomky sekund jsou volitelné. Sekundy jsou volitelné, pokud nejsou zadány zlomky sekund; v tomto případě se vyžadují sekundy. Pokud nejsou zadány sekundy nebo zlomky sekund, použije se místo toho výchozí hodnota nula.  
  
 Mezi symbolem DATETIME a datovou částí literálu může být libovolný počet mezer, ale žádné nové řádky.  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Interval  
 Časový literál je nezávislý na národním prostředí a skládá se pouze z časových částí. Časová část je povinná a neexistuje žádná výchozí hodnota. Musí mít formát HH: MM [: SS [. fffffff]], kde HH je hodnota hodiny mezi 0 a 23, MM je minutová hodnota mezi 0 a 59, SS je druhá hodnota mezi 0 a 59 a fffffff je druhá hodnota zlomku mezi 0 a 9999999. Všechny rozsahy hodnot jsou včetně. Zlomky sekund jsou volitelné. Sekundy jsou volitelné, pokud nejsou zadány zlomky sekund; v tomto případě se vyžadují sekundy. Pokud nejsou zadány sekundy nebo zlomky, použije se místo toho výchozí hodnota nula.  
  
 Mezi symbolem času a datovou částí literálu může být libovolný počet mezer, ale žádné nové řádky.  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 Literál DateTimeOffset je nezávislý na národním prostředí a skládá se z části data, časové části a posunuté části. Všechny části data, času a posunu jsou povinné a nejsou k dispozici žádné výchozí hodnoty. Část data musí mít formát RRRR-MM-DD, kde RRRR představuje čtyři číslo roku v hodnotě 0001 až 9999, MM je měsíc mezi 1 a 12 a DD je hodnota dne platná pro daný měsíc. Časová část musí mít formát HH: MM [: SS [. fffffff]], kde HH je hodnota hodiny mezi 0 a 23, MM je hodnota minuty mezi 0 a 59, SS je druhá hodnota mezi 0 a 59 a hodnota fffffff je desetinná sekunda mezi 0 a 9999999. Všechny rozsahy hodnot jsou včetně. Zlomky sekund jsou volitelné. Sekundy jsou volitelné, pokud nejsou zadány zlomky sekund; v tomto případě se vyžadují sekundy. Pokud nejsou zadány sekundy nebo zlomky, použije se místo toho výchozí hodnota nula. Část posunu musí mít formát {+&#124;-} hh: mm, kde hh a mm mají stejný význam jako v časové části. Rozsah posunu však musí být mezi-14:00 a + 14:00.  
  
 Mezi symbolem DATETIMEOFFSET a datovou částí literálu může být libovolný počet mezer, ale žádné nové řádky.  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> Platná hodnota literálu Entity SQL může klesnout mimo podporované rozsahy pro CLR nebo zdroj dat. Výsledkem může být výjimka  
  
## <a name="binary"></a>binární  
 Binární řetězcový literál je posloupnost hexadecimálních číslic oddělených jednoduchými uvozovkami za binárním znakem nebo symbolem zástupce `X` nebo `x`. Symbol zástupce `X` rozlišuje velká a malá písmena. Mezi klíčovým slovem `binary` a hodnotou binárního řetězce je povoleno nula nebo více mezer.  
  
 Šestnáctkové znaky se rozlišují i bez rozlišení velkých a malých písmen. Pokud se literál skládá z lichého počtu šestnáctkových číslic, bude literál zarovnán na další sudé číslo v šestnáctkové soustavě pomocí předpony literálu s hexadecimální nulou. Velikost binárního řetězce není v žádném formálním limitu.  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Hlavních  
 Literál `GUID` představuje globálně jedinečný identifikátor. Jedná se o sekvenci vytvořenou klíčovým slovem `GUID` následovanou šestnáctkovými číslicemi ve formátu, který je známý jako formát *registru* : 8-4-4-4-12 uzavřený v jednoduchých uvozovkách. Hexadecimální číslice rozlišují malá a velká písmena.  
  
 Mezi symbolem GUID a datovou částí literálu může být libovolný počet mezer, ale žádné nové řádky.  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
