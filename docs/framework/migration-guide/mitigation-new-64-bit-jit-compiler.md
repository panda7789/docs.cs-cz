---
title: 'Omezení rizik: Nové 64-bit JIT kompilátoru'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4edce9558cdbdd5937aa12866077210a91ee8494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391937"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Omezení rizik: Nové 64-bit JIT kompilátoru
Od verze rozhraní .NET Framework 4.6, modul runtime zahrnuje nové kompilátoru JIT 64-bit pro kompilaci za běhu. Tato změna nemá vliv kompilace s 32-bit kompilátoru za běhu.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Neočekávané chování nebo výjimky  
 V některých případech výsledky kompilace pomocí nové 64bitový kompilátor JIT v výjimku modulu runtime nebo v chování, které není dodržen při provádění kódu starší 64bitový kompilátor JIT zkompilují. Známé rozdíly zahrnují následující:  
  
> [!IMPORTANT]
>  Všechny tyto známé problémy mít byly řešeny v nové 64bitový kompilátor vydané s rozhraním .NET Framework 4.6.2. Většina mít také vyřeší ve vydáních služby rozhraní .NET Framework 4.6 a 4.6.1, které jsou součástí služby Windows Update. Můžete vyloučit tyto problémy zajištěním, které vaši verzi systému Windows je aktuální, nebo po upgradu na rozhraní .NET Framework 4.6.2.  
  
-   Za určitých podmínek může vyvolat operace rozbalení <xref:System.NullReferenceException> v sestavení pro vydání s optimalizací zapnutý.  
  
-   V některých případech může spuštění produkčním kódu v textu obsáhlou metodu throw <xref:System.StackOverflowException>.  
  
-   Za určitých podmínek struktury předána metodě, jsou považovány za odkazové typy místo typy hodnot v verzi sestavení. Jedním z projevů tohoto problému je, že jednotlivé položky v kolekci se objeví v neočekávaném pořadí.  
  
-   Za určitých podmínek, při porovnání <xref:System.UInt16> hodnoty sadou jejich rozšířené je nesprávný, pokud je povolená optimalizace.  
  
-   Za určitých podmínek, zejména při inicializaci pole hodnot, inicializace paměti pomocí <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instrukce může inicializovat paměť s nesprávnou hodnotu. To může způsobit buď v neošetřené výjimky nebo nesprávné výstup.  
  
-   Za určitých výjimečných podmínek, může vrátit testu podmíněného bit nesprávném <xref:System.Boolean> hodnotu nebo vyvolána výjimka, pokud jsou povolené optimalizace kompilátoru.  
  
-   Za určitých podmínek Pokud `if` příkaz se používá k testování pro podmínku před vstupem `try` bloku a ve výstupu z `try` bloku a stejné podmínku vyhodnotí v `catch` nebo `finally` bloku, nové 64bitový kompilátor JIT odebere `if` podmínky z `catch` nebo `finally` blokovat, když optimalizuje kódu. V důsledku toho code uvnitř `if` příkaz v `catch` nebo `finally` bezpodmínečně vykonání bloku.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Zmírnění dopadů známých problémů  
 Pokud narazíte na problémy uvedené výše, můžete je vyřešit pomocí některého z následujících akcí:  
  
-   Upgrade na rozhraní .NET Framework 4.6.2. Nové 64bitový kompilátor součástí rozhraní .NET Framework 4.6.2 řeší každý z těchto známých problémů.  
  
-   Zajistěte, aby byl vaši verzi systému Windows aktuální spuštěním služby Windows Update. Aktualizace služby rozhraní .NET Framework 4.6 a 4.6.1 se vztahují na všechny tyto problémy s výjimkou <xref:System.NullReferenceException> v rozbalení operace.  
  
-   Kompilace s starší 64bitový kompilátor JIT. Najdete v článku [zmírnění další problémy](#Other) části Další informace o tom, jak to udělat.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Zmírnění dopadů jiné problémy  
 Pokud narazíte na žádné jiné rozdíl v chování mezi kódem kompilovat s starší 64bitový kompilátor a nové 64bitový kompilátor JIT, nebo mezi ladění a vydání verze aplikace, které jsou kompilovat s novou 64bitový kompilátor JIT, můžete provést následující sestavovat aplikace pomocí starší 64bitový kompilátor JIT:  
  
-   Na základě jednotlivých aplikací, můžete přidat [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element konfiguračního souboru aplikace. Následující zakáže kompilaci s novou 64bitový kompilátor JIT a místo toho používá starší verze 64bitový kompilátor JIT.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   U každého uživatele zvlášť, můžete přidat `REG_DWORD` hodnotu s názvem `useLegacyJit` k `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče registru. Hodnota 1 povolí starší verze kompilátoru JIT 64-bit; Hodnota 0 zakáže ho a umožňuje nové 64bitový kompilátor JIT.  
  
-   U jednotlivých počítačů, můžete přidat `REG_DWORD` hodnotu s názvem `useLegacyJit` k `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíče registru. Hodnota 1 povolí starší verze kompilátoru JIT 64-bit; Hodnota 0 zakáže ho a umožňuje nové 64bitový kompilátor JIT.  
  
 Vám může také dejte nám vědět o problému pomocí hlášení chyby na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Viz také  
 [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 [\<useLegacyJit > elementu](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
