---
title: 'Zmírnění: nový 64 kompilátor JIT'
description: Seznamte se s novým 64 kompilátorem JIT, který je součástí .NET Framework 4,6 a neočekávané chování nebo výjimky, které mohou nastat během kompilace.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: f059cbdd3b2a66ac8a668b7b8a80d9ad1551fa64
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475226"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Zmírnění: nový 64 kompilátor JIT
Počínaje .NET Framework 4,6 obsahuje modul runtime nový 64 kompilátor JIT pro kompilaci za běhu. Tato změna nemá vliv na kompilaci s 32 kompilátorem JIT.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Neočekávané chování nebo výjimky  
 V některých případech kompilace s novým 64 kompilátorem JIT má za následek výjimku za běhu nebo v chování, které není pozorováno při provádění kódu zkompilovaného starším 64 kompilátorem JIT. Mezi známé rozdíly patří následující:  
  
> [!IMPORTANT]
> Všechny tyto známé problémy byly vyřešeny v novém 64 kompilátoru, který byl vydán s .NET Framework 4.6.2. K dispozici jsou také nejnovější verze .NET Framework 4,6 a 4.6.1, které jsou součástí web Windows Update. Tyto problémy můžete eliminovat tím, že zajistíte aktuálnost vaší verze Windows nebo upgradem na .NET Framework 4.6.2.  
  
- Za určitých podmínek může rozbalení operace vyvolat v sestavení vydaných <xref:System.NullReferenceException> verzí s zapnutou optimalizací.  
  
- V některých případech může provedení produkčního kódu v těle metody vyvolat výjimku <xref:System.StackOverflowException> .  
  
- Za určitých podmínek se struktury předané metodě považují jako typy odkazů spíše než typy hodnot v sestaveních vydaných verzí. Jedním z manifestů tohoto problému je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.  
  
- Za určitých podmínek <xref:System.UInt16> je porovnání hodnot s jejich vysokou bitovou sadou nesprávné, pokud je povolena optimalizace.  
  
- Za určitých podmínek, zejména při inicializaci hodnot pole, může inicializace paměti pomocí <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcí Il inicializovat paměť s nesprávnou hodnotou. Výsledkem může být Neošetřená výjimka nebo nesprávný výstup.  
  
- Za určitých vzácných podmínek může podmíněný bit test vracet nesprávnou <xref:System.Boolean> hodnotu nebo vyvolat výjimku, pokud jsou povoleny optimalizace kompilátoru.  
  
- Za určitých podmínek platí, že pokud `if` je příkaz použit k otestování podmínky před vstupem do `try` bloku a do ukončení z `try` bloku a stejná podmínka je vyhodnocena v `catch` bloku nebo `finally` , nový 64 kompilátor JIT `if` `catch` `finally` při optimalizaci kódu odstraní podmínku z bloku nebo. V důsledku toho je kód uvnitř `if` příkazu v `catch` `finally` bloku nebo proveden nepodmíněným způsobem.  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a>Zmírnění známých problémů  
 Pokud narazíte na výše uvedené problémy, můžete je vyřešit provedením následujících akcí:  
  
- Upgradujte na .NET Framework 4.6.2. Nový 64 kompilátor zahrnutý do .NET Framework 4.6.2 řeší všechny tyto známé problémy.  
  
- Zajistěte, aby byla verze Windows aktuální, a to spuštěním web Windows Update. Aktualizace služby .NET Framework 4,6 a 4.6.1 řeší každý z těchto problémů s výjimkou <xref:System.NullReferenceException> operace rozbalení.  
  
- Zkompiluje se starším 64 kompilátorem JIT. Další informace o tom, jak to udělat, najdete v části [zmírnění problémů s dalšími problémy](#Other) .  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a>Zmírnění jiných problémů  
 Pokud narazíte na jiné rozdíly v chování mezi kódem kompilovaným se starším 64 kompilátorem a novým 64 kompilátorem JIT, nebo mezi verzemi ladění a vydání vaší aplikace, které jsou zkompilovány pomocí nového 64-bitového kompilátoru JIT, můžete provést následující postup pro zkompilování aplikace se 64 starším 32bitovým kompilátorem JIT. :  
  
- Na základě jednotlivých aplikací můžete přidat [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) prvek do konfiguračního souboru aplikace. Následující zakáže kompilaci s novým 64 kompilátorem JIT a místo toho používá starší 64 kompilátor JIT.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Na základě jednotlivých uživatelů můžete do `REG_DWORD` klíče registru přidat hodnotu s názvem `useLegacyJit` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` . Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.  
  
- Na základě jednotlivých počítačů můžete do `REG_DWORD` klíče registru přidat hodnotu s názvem `useLegacyJit` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` . Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.  
  
 Můžete nám taky informovat o problému tím, že nahlásíte chybu na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
- [\<useLegacyJit>Objekt](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
