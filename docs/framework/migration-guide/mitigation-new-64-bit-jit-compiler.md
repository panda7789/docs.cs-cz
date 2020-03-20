---
title: 'Zmírnění: Nový 64bitový kompilátor JIT'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 883aaf032bde632b08f965d3450cfbea4feb8e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181255"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Zmírnění: Nový 64bitový kompilátor JIT
Počínaje rozhraním .NET Framework 4.6 obsahuje runtime nový 64bitový kompilátor JIT pro kompilaci just-in-time. Tato změna nemá vliv na kompilaci s 32bitovým kompilátorem JIT.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Neočekávané chování nebo výjimky  
 V některých případech kompilace s novým 64bitový kompilátor JIT výsledky v modulu runtime výjimku nebo v chování, které není pozorováno při provádění kódu zkompilovaného starší 64bitový kompilátor JIT. Známé rozdíly zahrnují následující:  
  
> [!IMPORTANT]
> Všechny tyto známé problémy byly vyřešeny v novém 64bitovém kompilátoru vydaném s rozhraním .NET Framework 4.6.2. Většina z nich byla také řešena ve verzích služby .NET Framework 4.6 a 4.6.1, které jsou součástí služby Windows Update. Tyto problémy můžete odstranit zajištěním, že vaše verze systému Windows je aktuální, nebo upgradem na rozhraní .NET Framework 4.6.2.  
  
- Za určitých podmínek může operace <xref:System.NullReferenceException> rozbalení vyvolat sestavení v verzi se zapnutou optimalizací.  
  
- V některých případech provádění výrobního kódu v těle <xref:System.StackOverflowException>velké metody může vyvolat .  
  
- Za určitých podmínek struktury předané metodě jsou považovány za typy odkazů, nikoli jako typy hodnot v sestaveních release. Jedním z projevů tohoto problému je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.  
  
- Za určitých <xref:System.UInt16> podmínek porovnání hodnot s jejich vysokou bitovou sadou je nesprávné, pokud je povolena optimalizace.  
  
- Za určitých podmínek, zejména při inicializaci hodnot pole, může inicializace paměti inicializací <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> il inicializace s nesprávnou hodnotou. To může mít za následek neošetřené výjimky nebo nesprávný výstup.  
  
- Za určitých výjimečných podmínek podmíněný <xref:System.Boolean> bitový test může vrátit nesprávnou hodnotu nebo vyvolat výjimku, pokud jsou povoleny optimalizace kompilátoru.  
  
- Za určitých podmínek, `if` pokud příkaz se používá `try` k testování podmínky před `try` zadáním bloku a výstupu `catch` z `finally` bloku a stejné podmínky je vyhodnocena `if` v `catch` nebo `finally` bloku, nový 64bitový kompilátor JIT odebere podmínku z nebo bloku při optimalizaci kódu. V důsledku toho je `if` kód `catch` uvnitř `finally` příkazu v bloku nebo proveden bezpodmínečně.  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a>Zmírnění známých problémů  
 Pokud narazíte na výše uvedené problémy, můžete je řešit některou z následujících akcí:  
  
- Upgrade na rozhraní .NET Framework 4.6.2. Nový 64bitový kompilátor, který je součástí rozhraní .NET Framework 4.6.2, řeší každý z těchto známých problémů.  
  
- Spuštěním služby Windows Update zajistíte aktuálnost vaší verze systému Windows. Aktualizace služby rozhraní .NET Framework 4.6 a 4.6.1 <xref:System.NullReferenceException> řeší každý z těchto problémů s výjimkou operace rozbalení.  
  
- Kompilujte se starším 64bitovým kompilátorem JIT. Další informace o tom, jak to provést, naleznete v části [Zmírnění dalších problémů.](#Other)  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a>Zmírnění dalších problémů  
 Pokud narazíte na jiný rozdíl v chování mezi kódem kompilovaným se starším 64bitovým kompilátorem a novým 64bitovým kompilátorem JIT nebo mezi ladicí mi a verzí aplikace, které jsou zkompilovány s novým 64bitovým kompilátorem JIT, můžete provést následující postup kompilace aplikace se starším 64bitovým kompilátorem JIT:  
  
- Na základě pro aplikaci, můžete přidat [ \<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) prvek do konfiguračního souboru aplikace. Následující zakáže kompilaci s novým 64bitovým kompilátorem JIT a místo toho používá starší 64bitový kompilátor JIT.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Na základě pro jednotlivé uživatele můžete `REG_DWORD` přidat `useLegacyJit` hodnotu pojmenovanou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` do klíče registru. Hodnota 1 umožňuje starší 64bitový kompilátor JIT; hodnota 0 zakáže a povolí nový 64bitový kompilátor JIT.  
  
- Na základě pro počítač můžete přidat `REG_DWORD` hodnotu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` pojmenovanou `useLegacyJit` do klíče registru. Hodnota 1 umožňuje starší 64bitový kompilátor JIT; hodnota 0 zakáže a povolí nový 64bitový kompilátor JIT.  
  
 Můžete nám také dát vědět o problému nahlášením chyby na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
- [\<useLegacyJit> Element](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
