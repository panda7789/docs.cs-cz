---
ms.openlocfilehash: 0237c848d71150aaea1f9de4f4b16a0cbbc4ab3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615636"
---
### <a name="new-64-bit-jit-compiler-in-the-net-framework-46"></a>Nový 64 kompilátor JIT v .NET Framework 4,6

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,6 se k kompilaci za běhu používá nový 64 kompilátor JIT. V některých případech je vyvolána Neočekávaná výjimka nebo je zjištěno jiné chování než při spuštění aplikace pomocí kompilátoru 32 nebo staršího 64 kompilátoru JIT. Tato změna nemá vliv na 32 kompilátor JIT. Mezi známé rozdíly patří následující:

- Za určitých podmínek může rozbalení operace vyvolat v sestavení vydaných <xref:System.NullReferenceException> verzí s zapnutou optimalizací.
- V některých případech může provedení produkčního kódu v těle metody vyvolat výjimku <xref:System.StackOverflowException> .
- Za určitých podmínek jsou struktury předané metodě považovány za typy odkazů, nikoli jako typy hodnot v sestaveních vydaných verzí. Jedním z manifestů tohoto problému je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.
- Za určitých podmínek <xref:System.UInt16> je porovnání hodnot s jejich vysokou bitovou sadou nesprávné, pokud je povolena optimalizace.
- Za určitých podmínek, zejména při inicializaci hodnot pole, může inicializace paměti pomocí <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcí Il inicializovat paměť s nesprávnou hodnotou. Výsledkem může být Neošetřená výjimka nebo nesprávný výstup.
- Za určitých vzácných podmínek může podmíněný bit test vracet nesprávnou <xref:System.Boolean> hodnotu nebo vyvolat výjimku, pokud jsou povoleny optimalizace kompilátoru.
- Za určitých podmínek platí, že pokud `if` je příkaz použit k otestování podmínky před vstupem do `try` bloku a do ukončení z `try` bloku a stejná podmínka je vyhodnocena v `catch` bloku nebo `finally` , nový 64 kompilátor JIT `if` `catch` `finally` při optimalizaci kódu odstraní podmínku z bloku nebo. V důsledku toho je kód uvnitř `if` příkazu v `catch` `finally` bloku nebo proveden nepodmíněným způsobem.

#### <a name="suggestion"></a>Návrh

**Zmírnění známých problémů** <br/> Pokud narazíte na výše uvedené problémy, můžete je vyřešit provedením následujících akcí:

- Upgradujte na .NET Framework 4.6.2. Nový 64 kompilátor zahrnutý do .NET Framework 4.6.2 řeší všechny tyto známé problémy.
- Zajistěte, aby byla verze Windows aktuální, a to spuštěním web Windows Update. Aktualizace služby .NET Framework 4,6 a 4.6.1 řeší každý z těchto problémů s výjimkou <xref:System.NullReferenceException> operace rozbalení.
- Zkompiluje se starším 64 kompilátorem JIT. Další informace o tom, jak to udělat, najdete v části **zmírnění problémů s dalšími problémy** .
**Zmírnění jiných problémů** <br/> Pokud narazíte na jiné rozdíly v chování mezi kódem kompilovaným se starším 64 kompilátorem a novým 64 kompilátorem JIT, nebo mezi verzemi ladění a vydání vaší aplikace, které jsou zkompilovány pomocí nového 64-bitového kompilátoru JIT, můžete provést následující postup pro zkompilování aplikace se 64 starším 32bitovým kompilátorem JIT. :

- Na základě jednotlivých aplikací můžete přidat [<](~/docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) prvek do konfiguračního souboru aplikace. Následující zakáže kompilaci s novým 64 kompilátorem JIT a místo toho používá starší 64 kompilátor JIT.

    ```xml
    <?xml version ="1.0"?>
    <configuration>
      <runtime>
       <useLegacyJit enabled="1" />
      </runtime>
    </configuration>
    ```

- Na základě jednotlivých uživatelů můžete do `REG_DWORD` klíče registru přidat hodnotu s názvem `useLegacyJit` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` . Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.
- Na základě jednotlivých počítačů můžete do `REG_DWORD` klíče registru přidat hodnotu s názvem `useLegacyJit` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` . Hodnota `1` povoluje starší 64 kompilátor JIT; hodnota `0` ji zakáže a povolí nový 64 kompilátor JIT.
Můžete nám taky informovat o problému tím, že nahlásíte chybu na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6         |
| Typ    | Změna cílení |
