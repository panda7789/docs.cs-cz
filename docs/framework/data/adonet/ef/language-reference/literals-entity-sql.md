---
title: Literály (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 71c77a3cb91d0981614e83221ad82d17067dc321
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643101"
---
# <a name="literals-entity-sql"></a>Literály (Entity SQL)
Toto téma popisuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporu pro literály.  
  
## <a name="null"></a>Null  
 Literál s hodnotou null se používá k reprezentování hodnota null pro libovolného typu. Literál null je kompatibilní s žádným typem.  
  
 Zadané hodnoty Null lze vytvořit pomocí přetypování nad literál s hodnotou null. Další informace najdete v tématu [PŘETYPOVÁNÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).  
  
 Pro pravidla o tom, kde zdarma s plovoucí desetinnou čárkou literály s hodnotou null lze použít, najdete v článku [literály s hodnotou Null a odvození typu proměnné](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boolean  
 Logická literály jsou reprezentovány klíčová slova `true` a `false`.  
  
## <a name="integer"></a>Integer  
 Literály celých čísel může být typu <xref:System.Int32> nebo <xref:System.Int64>. <xref:System.Int32> Literálu je řady číselných znaků. <xref:System.Int64> Literálu je řady číselných znaků, za nímž následuje velké písmeno L.  
  
## <a name="decimal"></a>Desetinné číslo  
 Číslo s pevnou desetinnou čárkou (decimální) je řady číselných znaků, tečku (.) a další řady číselných znaků, za nímž následuje velká písmena "M".  
  
## <a name="float-double"></a>Float, Double  
 Číslo dvojité přesnosti s plovoucí desetinnou čárkou bod je řada číselné znaky, tečky (.) a jiné řady číselných znaků může být za nímž následuje exponent. Jedné přesnosti čísla syntaxe, za nímž následuje malé f bod, čísla (nebo float) dvojité přesnosti s plovoucí desetinnou čárkou plovoucí desetinnou čárkou.  
  
## <a name="string"></a>String  
 Řetězec je posloupnost znaků uzavřený do uvozovek nahoře. Nabídek může být buď oba jedním uvozovky (`'`) nebo obě dvojité uvozovky ("). Znakové literály řetězce může být ve formátu Unicode nebo kódování Unicode. Chcete-li deklarovat literálu jako Unicode řetězec znaků, předpona literálu se velká písmena "N". Výchozí hodnota je řetězec literálů kódování Unicode. Může být žádné mezery mezi N a řetězcovou datovou část a N musí být uváděny velkými písmeny.  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DateTime  
 Literál datum a čas je nezávislý na národním prostředí a se skládá z část data a času část. Datum a čas jsou povinné a neexistují žádné výchozí hodnoty.  
  
 Část data musí mít formát: `YYYY` - `MM` - `DD`, kde `YYYY` je hodnota roku čtyřmístné 0001 až 9999, `MM` měsíc od 1 do 12 a `DD` je hodnota dne, který je platný pro daný měsíc `MM`.  
  
 Časovou část musí mít formát: `HH`:`MM`[:`SS`[.fffffff]], kde `HH` je hodina hodnota mezi 0 a 23, `MM` minut hodnotu od 0 do 59, `SS` je druhá hodnota mezi 0 a 59 a fffffff je desetinná druhá hodnota mezi 0 a 9999999. Všechny hodnoty rozsahy jsou včetně. Desetinné části sekund jsou volitelné. Pokud jsou uvedeny desetinné části sekund; jsou volitelné sekundy v takovém případě se vyžadují sekund. Pokud nejsou zadané sekund nebo zlomků sekund, použije se místo toho výchozí hodnotu nula.  
  
 Může existovat libovolný počet mezery mezi symboly data a času a datovou část, ale žádné nové řádky.  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Čas  
 Časový literál je nezávislý na národním prostředí a skládá z pouze část času. Časovou část je povinná a není žádná výchozí hodnota. Musí mít ve formátu hh: mm [: SS [.fffffff]], kde je hodina hodnotu mezi 0 a 23, MM je minuta hodnotu od 0 do 59, SS je druhá hodnota mezi 0 a 59 a fffffff je druhá část HH hodnotu mezi 0 a 9999999. Všechny hodnoty rozsahy jsou včetně. Desetinné části sekund jsou volitelné. Pokud jsou uvedeny desetinné části sekund; jsou volitelné sekundy v takovém případě se vyžadují sekund. Při sekund nebo zlomky nejsou zadané, použije se místo toho nastavená výchozí hodnota nula.  
  
 Může existovat libovolný počet mezer mezi symbol čas a datovou část, ale žádné nové řádky.  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 Datetimeoffset literálu je nezávislý na národním prostředí a skládá z část data, času část a posunu část. Datum, čas a posunu části jsou povinné a neexistují žádné výchozí hodnoty. Datum část musí mít formát rrrr-MM-DD, rrrr kde je hodnota roku čtyřmístné 0001 až 9999, MM je měsíc od 1 do 12 a DD je hodnota dne, který je platný pro daný měsíc. Část času, musí mít ve formátu hh: mm [: SS [.fffffff]], kde HH je hodina hodnotu mezi 0 a 23, MM minuty hodnotu mezi 0 a 59, SS je druhá hodnota mezi 0 a 59 a fffffff je desetinná druhá hodnota mezi 0 a 9999999. Všechny hodnoty rozsahy jsou včetně. Desetinné části sekund jsou volitelné. Pokud jsou uvedeny desetinné části sekund; jsou volitelné sekundy v takovém případě se vyžadují sekund. Při sekund nebo zlomky nejsou zadané, použije se místo toho nastavená výchozí hodnota nula. Posunutí část musí mít formát {+&#124;-} hh: mm, kde HH a MM mají stejný význam jako část času. Rozsah posunu, ale musí být mezi -14:00 a + 14:00  
  
 Může existovat libovolný počet mezery mezi symboly DATETIMEOFFSET a datovou část, ale žádné nové řádky.  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  Platná hodnota literálu Entity SQL nebude mimo podporovaný rozsah pro CLR nebo zdroj dat. To může způsobit výjimku  
  
## <a name="binary"></a>binární  
 Binární řetězcového literálu je posloupnost šestnáctkových číslic oddělených jednoduchých uvozovek a být následující binární klíčové slovo nebo symbol místní `X` nebo `x`. Symbol místní `X` velká a malá písmena. Nula nebo více mezer, které jsou povolené mezi klíčové slovo `binary` a binární řetězcovou hodnotu.  
  
 Šestnáctkové znaky jsou také malá a velká písmena. Pokud literál skládá z lichý počet šestnáctkových číslic, literál budou zarovnané na další i hexadecimální číslici vložením prefixu literál s hexadecimální nulu. Neexistuje žádné formální limit velikost binárního řetězce.  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Guid  
 A `GUID` literál představuje globálně jedinečný identifikátor. Je sekvence tvořen přidáním klíčového slova `GUID` a šestnáctkovými číslicemi ve formuláři říká *registru* formátu: 8-4-4-4-12 uzavřena do jednoduchých uvozovek. Hexadecimální číslice jsou malá a velká písmena.  
  
 Může existovat libovolný počet mezer mezi GUID symbol a datovou část, ale žádné nové řádky.  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Viz také:
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
