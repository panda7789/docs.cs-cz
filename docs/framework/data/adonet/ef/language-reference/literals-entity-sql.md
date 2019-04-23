---
title: Literály (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: bff9b1907d3424dc2e3df80480b6ab12f5ab9261
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209772"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="bfe69-102">Literály (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bfe69-102">Literals (Entity SQL)</span></span>
<span data-ttu-id="bfe69-103">Toto téma popisuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporu pro literály.</span><span class="sxs-lookup"><span data-stu-id="bfe69-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="bfe69-104">Null</span><span class="sxs-lookup"><span data-stu-id="bfe69-104">Null</span></span>  
 <span data-ttu-id="bfe69-105">Literál s hodnotou null se používá k reprezentování hodnota null pro libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="bfe69-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="bfe69-106">Literál null je kompatibilní s žádným typem.</span><span class="sxs-lookup"><span data-stu-id="bfe69-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="bfe69-107">Zadané hodnoty Null lze vytvořit pomocí přetypování nad literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="bfe69-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="bfe69-108">Další informace najdete v tématu [PŘETYPOVÁNÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bfe69-108">For more information, see [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="bfe69-109">Pro pravidla o tom, kde zdarma s plovoucí desetinnou čárkou literály s hodnotou null lze použít, najdete v článku [literály s hodnotou Null a odvození typu proměnné](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bfe69-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="bfe69-110">Boolean</span><span class="sxs-lookup"><span data-stu-id="bfe69-110">Boolean</span></span>  
 <span data-ttu-id="bfe69-111">Logická literály jsou reprezentovány klíčová slova `true` a `false`.</span><span class="sxs-lookup"><span data-stu-id="bfe69-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="bfe69-112">Integer</span><span class="sxs-lookup"><span data-stu-id="bfe69-112">Integer</span></span>  
 <span data-ttu-id="bfe69-113">Literály celých čísel může být typu <xref:System.Int32> nebo <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="bfe69-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="bfe69-114"><xref:System.Int32> Literálu je řady číselných znaků.</span><span class="sxs-lookup"><span data-stu-id="bfe69-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="bfe69-115"><xref:System.Int64> Literálu je řady číselných znaků, za nímž následuje velké písmeno L.</span><span class="sxs-lookup"><span data-stu-id="bfe69-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="bfe69-116">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="bfe69-116">Decimal</span></span>  
 <span data-ttu-id="bfe69-117">Číslo s pevnou desetinnou čárkou (decimální) je řady číselných znaků, tečku (.) a další řady číselných znaků, za nímž následuje velká písmena "M".</span><span class="sxs-lookup"><span data-stu-id="bfe69-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="bfe69-118">Float, Double</span><span class="sxs-lookup"><span data-stu-id="bfe69-118">Float, Double</span></span>  
 <span data-ttu-id="bfe69-119">Číslo dvojité přesnosti s plovoucí desetinnou čárkou bod je řada číselné znaky, tečky (.) a jiné řady číselných znaků může být za nímž následuje exponent.</span><span class="sxs-lookup"><span data-stu-id="bfe69-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="bfe69-120">Jedné přesnosti čísla syntaxe, za nímž následuje malé f bod, čísla (nebo float) dvojité přesnosti s plovoucí desetinnou čárkou plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="bfe69-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="bfe69-121">String</span><span class="sxs-lookup"><span data-stu-id="bfe69-121">String</span></span>  
 <span data-ttu-id="bfe69-122">Řetězec je posloupnost znaků uzavřený do uvozovek nahoře.</span><span class="sxs-lookup"><span data-stu-id="bfe69-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="bfe69-123">Nabídek může být buď oba jedním uvozovky (`'`) nebo obě dvojité uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="bfe69-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="bfe69-124">Znakové literály řetězce může být ve formátu Unicode nebo kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="bfe69-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="bfe69-125">Chcete-li deklarovat literálu jako Unicode řetězec znaků, předpona literálu se velká písmena "N".</span><span class="sxs-lookup"><span data-stu-id="bfe69-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="bfe69-126">Výchozí hodnota je řetězec literálů kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="bfe69-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="bfe69-127">Může být žádné mezery mezi N a řetězcovou datovou část a N musí být uváděny velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="bfe69-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="bfe69-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="bfe69-128">DateTime</span></span>  
 <span data-ttu-id="bfe69-129">Literál datum a čas je nezávislý na národním prostředí a se skládá z část data a času část.</span><span class="sxs-lookup"><span data-stu-id="bfe69-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="bfe69-130">Datum a čas jsou povinné a neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfe69-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="bfe69-131">Část data musí mít formát: `YYYY` - `MM` - `DD`, kde `YYYY` je hodnota roku čtyřmístné 0001 až 9999, `MM` měsíc od 1 do 12 a `DD` je hodnota dne, který je platný pro daný měsíc `MM`.</span><span class="sxs-lookup"><span data-stu-id="bfe69-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="bfe69-132">Časovou část musí mít formát: `HH`:`MM`[:`SS`[.fffffff]], kde `HH` je hodina hodnota mezi 0 a 23, `MM` minut hodnotu od 0 do 59, `SS` je druhá hodnota mezi 0 a 59 a fffffff je desetinná druhá hodnota mezi 0 a 9999999.</span><span class="sxs-lookup"><span data-stu-id="bfe69-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="bfe69-133">Všechny hodnoty rozsahy jsou včetně.</span><span class="sxs-lookup"><span data-stu-id="bfe69-133">All value ranges are inclusive.</span></span> <span data-ttu-id="bfe69-134">Desetinné části sekund jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="bfe69-134">Fractional seconds are optional.</span></span> <span data-ttu-id="bfe69-135">Pokud jsou uvedeny desetinné části sekund; jsou volitelné sekundy v takovém případě se vyžadují sekund.</span><span class="sxs-lookup"><span data-stu-id="bfe69-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="bfe69-136">Pokud nejsou zadané sekund nebo zlomků sekund, použije se místo toho výchozí hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="bfe69-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="bfe69-137">Může existovat libovolný počet mezery mezi symboly data a času a datovou část, ale žádné nové řádky.</span><span class="sxs-lookup"><span data-stu-id="bfe69-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="bfe69-138">Čas</span><span class="sxs-lookup"><span data-stu-id="bfe69-138">Time</span></span>  
 <span data-ttu-id="bfe69-139">Časový literál je nezávislý na národním prostředí a skládá z pouze část času.</span><span class="sxs-lookup"><span data-stu-id="bfe69-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="bfe69-140">Časovou část je povinná a není žádná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="bfe69-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="bfe69-141">Musí mít ve formátu hh: mm [: SS [.fffffff]], kde je hodina hodnotu mezi 0 a 23, MM je minuta hodnotu od 0 do 59, SS je druhá hodnota mezi 0 a 59 a fffffff je druhá část HH hodnotu mezi 0 a 9999999.</span><span class="sxs-lookup"><span data-stu-id="bfe69-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="bfe69-142">Všechny hodnoty rozsahy jsou včetně.</span><span class="sxs-lookup"><span data-stu-id="bfe69-142">All value ranges are inclusive.</span></span> <span data-ttu-id="bfe69-143">Desetinné části sekund jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="bfe69-143">Fractional seconds are optional.</span></span> <span data-ttu-id="bfe69-144">Pokud jsou uvedeny desetinné části sekund; jsou volitelné sekundy v takovém případě se vyžadují sekund.</span><span class="sxs-lookup"><span data-stu-id="bfe69-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="bfe69-145">Při sekund nebo zlomky nejsou zadané, použije se místo toho nastavená výchozí hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="bfe69-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="bfe69-146">Může existovat libovolný počet mezer mezi symbol čas a datovou část, ale žádné nové řádky.</span><span class="sxs-lookup"><span data-stu-id="bfe69-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="bfe69-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="bfe69-147">DateTimeOffset</span></span>  
 <span data-ttu-id="bfe69-148">Datetimeoffset literálu je nezávislý na národním prostředí a skládá z část data, času část a posunu část.</span><span class="sxs-lookup"><span data-stu-id="bfe69-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="bfe69-149">Datum, čas a posunu části jsou povinné a neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfe69-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="bfe69-150">Datum část musí mít formát rrrr-MM-DD, rrrr kde je hodnota roku čtyřmístné 0001 až 9999, MM je měsíc od 1 do 12 a DD je hodnota dne, který je platný pro daný měsíc.</span><span class="sxs-lookup"><span data-stu-id="bfe69-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="bfe69-151">Část času, musí mít ve formátu hh: mm [: SS [.fffffff]], kde HH je hodina hodnotu mezi 0 a 23, MM minuty hodnotu mezi 0 a 59, SS je druhá hodnota mezi 0 a 59 a fffffff je desetinná druhá hodnota mezi 0 a 9999999.</span><span class="sxs-lookup"><span data-stu-id="bfe69-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="bfe69-152">Všechny hodnoty rozsahy jsou včetně.</span><span class="sxs-lookup"><span data-stu-id="bfe69-152">All value ranges are inclusive.</span></span> <span data-ttu-id="bfe69-153">Desetinné části sekund jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="bfe69-153">Fractional seconds are optional.</span></span> <span data-ttu-id="bfe69-154">Pokud jsou uvedeny desetinné části sekund; jsou volitelné sekundy v takovém případě se vyžadují sekund.</span><span class="sxs-lookup"><span data-stu-id="bfe69-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="bfe69-155">Při sekund nebo zlomky nejsou zadané, použije se místo toho nastavená výchozí hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="bfe69-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="bfe69-156">Posunutí část musí mít formát {+&#124;-} hh: mm, kde HH a MM mají stejný význam jako část času.</span><span class="sxs-lookup"><span data-stu-id="bfe69-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="bfe69-157">Rozsah posunu, ale musí být mezi -14:00 a + 14:00</span><span class="sxs-lookup"><span data-stu-id="bfe69-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="bfe69-158">Může existovat libovolný počet mezery mezi symboly DATETIMEOFFSET a datovou část, ale žádné nové řádky.</span><span class="sxs-lookup"><span data-stu-id="bfe69-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  <span data-ttu-id="bfe69-159">Platná hodnota literálu Entity SQL nebude mimo podporovaný rozsah pro CLR nebo zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="bfe69-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="bfe69-160">To může způsobit výjimku</span><span class="sxs-lookup"><span data-stu-id="bfe69-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="bfe69-161">binární</span><span class="sxs-lookup"><span data-stu-id="bfe69-161">Binary</span></span>  
 <span data-ttu-id="bfe69-162">Binární řetězcového literálu je posloupnost šestnáctkových číslic oddělených jednoduchých uvozovek a být následující binární klíčové slovo nebo symbol místní `X` nebo `x`.</span><span class="sxs-lookup"><span data-stu-id="bfe69-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="bfe69-163">Symbol místní `X` velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="bfe69-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="bfe69-164">Nula nebo více mezer, které jsou povolené mezi klíčové slovo `binary` a binární řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bfe69-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="bfe69-165">Šestnáctkové znaky jsou také malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="bfe69-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="bfe69-166">Pokud literál skládá z lichý počet šestnáctkových číslic, literál budou zarovnané na další i hexadecimální číslici vložením prefixu literál s hexadecimální nulu.</span><span class="sxs-lookup"><span data-stu-id="bfe69-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="bfe69-167">Neexistuje žádné formální limit velikost binárního řetězce.</span><span class="sxs-lookup"><span data-stu-id="bfe69-167">There is no formal limit on the size of the binary string.</span></span>  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="bfe69-168">Guid</span><span class="sxs-lookup"><span data-stu-id="bfe69-168">Guid</span></span>  
 <span data-ttu-id="bfe69-169">A `GUID` literál představuje globálně jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="bfe69-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="bfe69-170">Je sekvence tvořen přidáním klíčového slova `GUID` a šestnáctkovými číslicemi ve formuláři říká *registru* formátu: 8-4-4-4-12 uzavřena do jednoduchých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="bfe69-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="bfe69-171">Hexadecimální číslice jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="bfe69-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="bfe69-172">Může existovat libovolný počet mezer mezi GUID symbol a datovou část, ale žádné nové řádky.</span><span class="sxs-lookup"><span data-stu-id="bfe69-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfe69-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfe69-173">See also</span></span>

- [<span data-ttu-id="bfe69-174">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bfe69-174">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
