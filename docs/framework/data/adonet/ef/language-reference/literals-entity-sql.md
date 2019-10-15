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
# <a name="literals-entity-sql"></a><span data-ttu-id="cdb26-102">Literály (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cdb26-102">Literals (Entity SQL)</span></span>
<span data-ttu-id="cdb26-103">Toto téma popisuje podporu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pro literály.</span><span class="sxs-lookup"><span data-stu-id="cdb26-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="cdb26-104">Null</span><span class="sxs-lookup"><span data-stu-id="cdb26-104">Null</span></span>  
 <span data-ttu-id="cdb26-105">Literál null se používá k reprezentaci hodnoty null pro libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="cdb26-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="cdb26-106">Literál s hodnotou null je kompatibilní s jakýmkoli typem.</span><span class="sxs-lookup"><span data-stu-id="cdb26-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="cdb26-107">Typové hodnoty null lze vytvořit přetypováním přes literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="cdb26-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="cdb26-108">Další informace najdete v tématu [přetypování](cast-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cdb26-108">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="cdb26-109">Pravidla o tom, kde lze použít bezplatné plovoucí literály null, naleznete v tématu [literály s hodnotou null a odvození typu](null-literals-and-type-inference-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cdb26-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="cdb26-110">Boolean</span><span class="sxs-lookup"><span data-stu-id="cdb26-110">Boolean</span></span>  
 <span data-ttu-id="cdb26-111">Logické literály jsou reprezentovány klíčovými slovy `true` a `false`.</span><span class="sxs-lookup"><span data-stu-id="cdb26-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="cdb26-112">Integer</span><span class="sxs-lookup"><span data-stu-id="cdb26-112">Integer</span></span>  
 <span data-ttu-id="cdb26-113">Celočíselné literály mohou být typu <xref:System.Int32> nebo <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="cdb26-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="cdb26-114">Literál <xref:System.Int32> je řada číselných znaků.</span><span class="sxs-lookup"><span data-stu-id="cdb26-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="cdb26-115">Literál <xref:System.Int64> je série číselných znaků následovaných velkým L.</span><span class="sxs-lookup"><span data-stu-id="cdb26-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="cdb26-116">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="cdb26-116">Decimal</span></span>  
 <span data-ttu-id="cdb26-117">Číslo s pevnou desetinnou čárkou (desítkově) je série číselných znaků, tečka (.) a další řada číselných znaků následovaných velkým písmenem "M".</span><span class="sxs-lookup"><span data-stu-id="cdb26-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="cdb26-118">Float, Double</span><span class="sxs-lookup"><span data-stu-id="cdb26-118">Float, Double</span></span>  
 <span data-ttu-id="cdb26-119">Číslo s plovoucí desetinnou čárkou a dvojitou přesností je řada číselných znaků, tečka (.) a další řada číselných znaků, které jsou pravděpodobně následovány exponentem.</span><span class="sxs-lookup"><span data-stu-id="cdb26-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="cdb26-120">Číslo s plovoucí desetinnou čárkou s jednoduchou přesností (neboli float) je syntaxe čísla s plovoucí desetinnou čárkou s dvojitou přesností následovaný malým písmenem f.</span><span class="sxs-lookup"><span data-stu-id="cdb26-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="cdb26-121">String</span><span class="sxs-lookup"><span data-stu-id="cdb26-121">String</span></span>  
 <span data-ttu-id="cdb26-122">Řetězec je řada znaků uzavřených v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="cdb26-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="cdb26-123">Uvozovky mohou být buď jednoduché (`'`), nebo obě dvojité uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="cdb26-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="cdb26-124">Řetězcové literály znaků můžou být Unicode nebo jiné než Unicode.</span><span class="sxs-lookup"><span data-stu-id="cdb26-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="cdb26-125">Chcete-li deklarovat řetězcový literál znaků jako Unicode, zaprefixujte literál s velkým písmenem "N".</span><span class="sxs-lookup"><span data-stu-id="cdb26-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="cdb26-126">Výchozí hodnoty jsou řetězcové literály, které nejsou znakové sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="cdb26-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="cdb26-127">Mezi N a datovou částí literálu řetězce nemůže být žádná mezera a N musí být velká.</span><span class="sxs-lookup"><span data-stu-id="cdb26-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="cdb26-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="cdb26-128">DateTime</span></span>  
 <span data-ttu-id="cdb26-129">Literál DateTime je nezávislý na národním prostředí a skládá se z části data a času.</span><span class="sxs-lookup"><span data-stu-id="cdb26-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="cdb26-130">Části data a času jsou povinné a nejsou k dispozici žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cdb26-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="cdb26-131">Část data musí mít formát: `YYYY` @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4, kde `YYYY` je hodnota roku v 9999 rozmezí 1 až 12 až `DD` @no__t, což je hodnota dne platná pro daný měsíc `MM`.</span><span class="sxs-lookup"><span data-stu-id="cdb26-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="cdb26-132">Časový interval musí mít formát: `HH`: `MM` [: `SS` [. fffffff]], kde `HH` je hodnota hodiny mezi 0 a 23, `MM` je minutová hodnota mezi 0 a 59, `SS` je druhá hodnota mezi 0 a 59 a fffffff je desetinná sekundová hodnota. mezi 0 a 9999999.</span><span class="sxs-lookup"><span data-stu-id="cdb26-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="cdb26-133">Všechny rozsahy hodnot jsou včetně.</span><span class="sxs-lookup"><span data-stu-id="cdb26-133">All value ranges are inclusive.</span></span> <span data-ttu-id="cdb26-134">Zlomky sekund jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="cdb26-134">Fractional seconds are optional.</span></span> <span data-ttu-id="cdb26-135">Sekundy jsou volitelné, pokud nejsou zadány zlomky sekund; v tomto případě se vyžadují sekundy.</span><span class="sxs-lookup"><span data-stu-id="cdb26-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="cdb26-136">Pokud nejsou zadány sekundy nebo zlomky sekund, použije se místo toho výchozí hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="cdb26-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="cdb26-137">Mezi symbolem DATETIME a datovou částí literálu může být libovolný počet mezer, ale žádné nové řádky.</span><span class="sxs-lookup"><span data-stu-id="cdb26-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="cdb26-138">Interval</span><span class="sxs-lookup"><span data-stu-id="cdb26-138">Time</span></span>  
 <span data-ttu-id="cdb26-139">Časový literál je nezávislý na národním prostředí a skládá se pouze z časových částí.</span><span class="sxs-lookup"><span data-stu-id="cdb26-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="cdb26-140">Časová část je povinná a neexistuje žádná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="cdb26-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="cdb26-141">Musí mít formát HH: MM [: SS [. fffffff]], kde HH je hodnota hodiny mezi 0 a 23, MM je minutová hodnota mezi 0 a 59, SS je druhá hodnota mezi 0 a 59 a fffffff je druhá hodnota zlomku mezi 0 a 9999999.</span><span class="sxs-lookup"><span data-stu-id="cdb26-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="cdb26-142">Všechny rozsahy hodnot jsou včetně.</span><span class="sxs-lookup"><span data-stu-id="cdb26-142">All value ranges are inclusive.</span></span> <span data-ttu-id="cdb26-143">Zlomky sekund jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="cdb26-143">Fractional seconds are optional.</span></span> <span data-ttu-id="cdb26-144">Sekundy jsou volitelné, pokud nejsou zadány zlomky sekund; v tomto případě se vyžadují sekundy.</span><span class="sxs-lookup"><span data-stu-id="cdb26-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="cdb26-145">Pokud nejsou zadány sekundy nebo zlomky, použije se místo toho výchozí hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="cdb26-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="cdb26-146">Mezi symbolem času a datovou částí literálu může být libovolný počet mezer, ale žádné nové řádky.</span><span class="sxs-lookup"><span data-stu-id="cdb26-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="cdb26-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="cdb26-147">DateTimeOffset</span></span>  
 <span data-ttu-id="cdb26-148">Literál DateTimeOffset je nezávislý na národním prostředí a skládá se z části data, časové části a posunuté části.</span><span class="sxs-lookup"><span data-stu-id="cdb26-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="cdb26-149">Všechny části data, času a posunu jsou povinné a nejsou k dispozici žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cdb26-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="cdb26-150">Část data musí mít formát RRRR-MM-DD, kde RRRR představuje čtyři číslo roku v hodnotě 0001 až 9999, MM je měsíc mezi 1 a 12 a DD je hodnota dne platná pro daný měsíc.</span><span class="sxs-lookup"><span data-stu-id="cdb26-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="cdb26-151">Časová část musí mít formát HH: MM [: SS [. fffffff]], kde HH je hodnota hodiny mezi 0 a 23, MM je hodnota minuty mezi 0 a 59, SS je druhá hodnota mezi 0 a 59 a hodnota fffffff je desetinná sekunda mezi 0 a 9999999.</span><span class="sxs-lookup"><span data-stu-id="cdb26-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="cdb26-152">Všechny rozsahy hodnot jsou včetně.</span><span class="sxs-lookup"><span data-stu-id="cdb26-152">All value ranges are inclusive.</span></span> <span data-ttu-id="cdb26-153">Zlomky sekund jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="cdb26-153">Fractional seconds are optional.</span></span> <span data-ttu-id="cdb26-154">Sekundy jsou volitelné, pokud nejsou zadány zlomky sekund; v tomto případě se vyžadují sekundy.</span><span class="sxs-lookup"><span data-stu-id="cdb26-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="cdb26-155">Pokud nejsou zadány sekundy nebo zlomky, použije se místo toho výchozí hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="cdb26-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="cdb26-156">Část posunu musí mít formát {+&#124;-} hh: mm, kde hh a mm mají stejný význam jako v časové části.</span><span class="sxs-lookup"><span data-stu-id="cdb26-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="cdb26-157">Rozsah posunu však musí být mezi-14:00 a + 14:00.</span><span class="sxs-lookup"><span data-stu-id="cdb26-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="cdb26-158">Mezi symbolem DATETIMEOFFSET a datovou částí literálu může být libovolný počet mezer, ale žádné nové řádky.</span><span class="sxs-lookup"><span data-stu-id="cdb26-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="cdb26-159">Platná hodnota literálu Entity SQL může klesnout mimo podporované rozsahy pro CLR nebo zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="cdb26-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="cdb26-160">Výsledkem může být výjimka</span><span class="sxs-lookup"><span data-stu-id="cdb26-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="cdb26-161">binární</span><span class="sxs-lookup"><span data-stu-id="cdb26-161">Binary</span></span>  
 <span data-ttu-id="cdb26-162">Binární řetězcový literál je posloupnost hexadecimálních číslic oddělených jednoduchými uvozovkami za binárním znakem nebo symbolem zástupce `X` nebo `x`.</span><span class="sxs-lookup"><span data-stu-id="cdb26-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="cdb26-163">Symbol zástupce `X` rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="cdb26-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="cdb26-164">Mezi klíčovým slovem `binary` a hodnotou binárního řetězce je povoleno nula nebo více mezer.</span><span class="sxs-lookup"><span data-stu-id="cdb26-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="cdb26-165">Šestnáctkové znaky se rozlišují i bez rozlišení velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="cdb26-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="cdb26-166">Pokud se literál skládá z lichého počtu šestnáctkových číslic, bude literál zarovnán na další sudé číslo v šestnáctkové soustavě pomocí předpony literálu s hexadecimální nulou.</span><span class="sxs-lookup"><span data-stu-id="cdb26-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="cdb26-167">Velikost binárního řetězce není v žádném formálním limitu.</span><span class="sxs-lookup"><span data-stu-id="cdb26-167">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="cdb26-168">Hlavních</span><span class="sxs-lookup"><span data-stu-id="cdb26-168">Guid</span></span>  
 <span data-ttu-id="cdb26-169">Literál `GUID` představuje globálně jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="cdb26-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="cdb26-170">Jedná se o sekvenci vytvořenou klíčovým slovem `GUID` následovanou šestnáctkovými číslicemi ve formátu, který je známý jako formát *registru* : 8-4-4-4-12 uzavřený v jednoduchých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="cdb26-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="cdb26-171">Hexadecimální číslice rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="cdb26-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="cdb26-172">Mezi symbolem GUID a datovou částí literálu může být libovolný počet mezer, ale žádné nové řádky.</span><span class="sxs-lookup"><span data-stu-id="cdb26-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdb26-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdb26-173">See also</span></span>

- [<span data-ttu-id="cdb26-174">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cdb26-174">Entity SQL Overview</span></span>](entity-sql-overview.md)
