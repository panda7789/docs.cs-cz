---
title: 'Omezení rizik: Nový kompilátor JIT 64-bit'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22c98e41624abc931bd03e4ddea09ed55d0d3f39
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648487"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Omezení rizik: Nový kompilátor JIT 64-bit
Od verze rozhraní .NET Framework 4.6, modul runtime obsahuje nové 64-bit kompilátor JIT kompilace just-in-time. Tato změna neovlivní kompilace s kompilátorem JIT 32-bit.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Neočekávané chování nebo výjimky  
 V některých případech se výsledky kompilace pomocí nového 64bitového kompilátoru JIT v výjimku při běhu nebo chování, které není dodržena při provádění kódu, které jsou kompilovány pomocí kompilátoru JIT starší 64-bit. Známé rozdíly patří následující:  
  
> [!IMPORTANT]
>  Vyřeší všechny tyto známé problémy v nového 64bitového kompilátoru vydané s použitím rozhraní .NET Framework 4.6.2. Většina také vyřeší služba verze rozhraní .NET Framework 4.6 a 4.6.1, které jsou součástí Windows Update. Můžete vyloučit tyto problémy tím, že zajišťuje, které vaši verzi systému Windows je aktuální, nebo po upgradu na rozhraní .NET Framework 4.6.2.  
  
- Za určitých podmínek může vyvolat operace rozbalení <xref:System.NullReferenceException> v sestaveních pro vydání s optimalizací zapnuté.  
  
- V některých případech se může vyvolat provádění kódu v těle metody velké <xref:System.StackOverflowException>.  
  
- Za určitých podmínek struktury předáno metodě, jsou považovány za typy odkazů spíše než typy hodnot ve verzi sestavení. Jedním z projevy tento problém je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.  
  
- Za určitých podmínek, porovnání <xref:System.UInt16> hodnoty s jejich rozšířené nastavení je nesprávné v případě, že je povolena optimalizace.  
  
- Za určitých podmínek, zejména při inicializaci pole hodnot, inicializace paměti <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukce IL může inicializovat paměť s nesprávnou hodnotu. To může vést neošetřené výjimce nebo nesprávný výstup.  
  
- Za určitých podmínek výjimečných bit podmíněný test může vrátit nesprávná <xref:System.Boolean> hodnotu nebo vyvolat výjimku, pokud jsou povolené optimalizace kompilátoru.  
  
- Za určitých podmínek Pokud `if` příkaz slouží k otestování pro podmínku před vstupem `try` bloku a ve výstupu z `try` bloku a stejná podmínka je vyhodnocena v `catch` nebo `finally` bloku, nové Odebere 64bitového JIT kompilátoru `if` podmínky z `catch` nebo `finally` blokovat, pokud optimalizuje kód. V důsledku toho kód `if` příkaz v `catch` nebo `finally` bloku je bezpodmínečně provedeny.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Zmírnění dopadů známých problémů  
 Pokud narazíte na problémy uvedené výše, abyste mohli vyřešit pomocí některého z následujících akcí:  
  
- Upgrade na rozhraní .NET Framework 4.6.2. Nový 64bitový kompilátor rozhraní .NET Framework 4.6.2 je součástí adresy každé z těchto známých problémů.  
  
- Ujistěte se, že je vaše verze Windows aktuální spuštěním aktualizace Windows. Aktualizace služeb rozhraní .NET Framework 4.6 a 4.6.1 se vztahují na všechny tyto problémy s výjimkou <xref:System.NullReferenceException> v operace rozbalení.  
  
- Kompilovat s starší 64bitovým kompilátorem JIT. Zobrazit [zmírnění problémů s jinými problémy](#Other) části Další informace o tom, jak to provést.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Zmírnění problémů s jinými problémy  
 Pokud narazíte na jakékoli další rozdíl v chování mezi kód zkompilovaný s starší 64bitovým kompilátorem a nového 64bitového kompilátoru JIT, nebo ladění a verze vydání aplikace, které jsou kompilovány pomocí nového 64bitového kompilátoru JIT, vám pomůžou následující aplikace s využitím starší 64bitového kompilátoru JIT kompilace:  
  
- Na základě jednotlivých aplikací, můžete přidat [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) prvku do konfiguračního souboru aplikace. Následující zakazuje kompilaci pomocí nového 64bitového kompilátoru JIT a místo toho používá starší verzi 64bitového kompilátoru JIT.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Na základě jednotlivých uživatelů můžete přidat `REG_DWORD` hodnotu s názvem `useLegacyJit` k `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče registru. Hodnota 1 povolí starší verzi kompilátoru JIT 64-bit; Hodnota 0 zakáže a umožňuje nové 64bitovým kompilátorem JIT.  
  
- Na základě vázaná na počítač, můžete přidat `REG_DWORD` hodnotu s názvem `useLegacyJit` k `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíče registru. Hodnota 1 povolí starší verzi kompilátoru JIT 64-bit; Hodnota 0 zakáže a umožňuje nové 64bitovým kompilátorem JIT.  
  
 Vám může také dejte nám vědět o problému pomocí hlášení chyby na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Viz také:

- [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [\<useLegacyJit> Element](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
