---
title: Bezpečnostní problémy v generování reflexe
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- emitting dynamic assemblies, security
- reflection emit, security
- reflection emit, partial trust scenarios
- partial trust,emitting dynamic methods
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- dynamic assemblies, security
ms.assetid: 0f8bf8fa-b993-478f-87ab-1a1a7976d298
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2995e64d9e8eed365498bcbc1047a321edc10c5
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489728"
---
# <a name="security-issues-in-reflection-emit"></a>Bezpečnostní problémy v generování reflexe
Rozhraní .NET Framework poskytuje tři způsoby, jak vygenerovat jazyk Microsoft intermediate language (MSIL), každý s vlastní problémy se zabezpečením:  
  
- [Dynamická sestavení](#Dynamic_Assemblies)  
  
- [Anonymně hostované dynamické metody](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Dynamické metody, které jsou přidružené k existující sestavení](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Bez ohledu na způsob generování dynamických kódu spouštění generovaný kód vyžaduje všechna oprávnění, které jsou vyžadovány typy a metody, které používá generovaného kódu.  
  
> [!NOTE]
>  S následných verzích rozhraní .NET Framework došlo ke změně oprávnění, které jsou požadovány pro odráží v kódu a vytváření kódu. Zobrazit [informace o verzi](#Version_Information)dále v tomto tématu.  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>Dynamická sestavení  
 Dynamické sestavení se vytvářejí pomocí přetížení <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> metody. Většina přetížení této metody jsou zastaralé v rozhraní .NET Framework 4, z důvodu odstranění zásad zabezpečení počítače. (Viz [změny zabezpečení](../../../docs/framework/security/security-changes.md).) Zbývající přetížení může provést všechny kódu, bez ohledu na úroveň důvěryhodnosti. Tato přetížení spadají do dvou skupin: ty, které určují seznam atributů, které chcete použít na dynamické sestavení při jeho vytváření a ty, které nepodporují. Pokud nezadáte model transparentnosti pro sestavení, s použitím <xref:System.Security.SecurityRulesAttribute> atribut při vytváření, model transparentnosti je zděděno od emitujícího sestavení.  
  
> [!NOTE]
>  Atributy, které se vztahují na dynamické sestavení po vytvoření s použitím <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> metody neprojeví až do sestavení byl uložen na disk a opětovném načtení do paměti.  
  
 Kód v dynamickém sestavení můžete přistupovat k viditelné typy a členy v jiných sestaveních.  
  
> [!NOTE]
>  Nepoužívejte dynamické sestavení <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> a <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznaky, které umožňují dynamickým metodám přístup k neveřejným typům a členům.  
  
 Přechodné dynamické sestavení jsou vytvořené v paměti a nikdy uloženo na disk, takže vyžadují žádné přístupová oprávnění k souboru. Uložení na disk dynamického sestavení vyžaduje <xref:System.Security.Permissions.FileIOPermission> s příslušnými příznaky.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generování dynamických sestavení z částečně důvěryhodného kódu  
 Vezměte v úvahu podmínky, ve kterých sestavení s oprávněními Internet generovat přechodné dynamické sestavení a jeho kód spustit:  
  
- Dynamické sestavení používá pouze veřejné typy a členy jiná sestavení.  
  
- Oprávnění potřebnou pro tyto typy a členy jsou součástí sady udělení částečně důvěryhodné sestavení.  
  
- Sestavení není uložen na disk.  
  
- Ladění nejsou generovány symboly. (`Internet` a `LocalIntranet` sady oprávnění nezahrnují potřebná oprávnění.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonymně hostované dynamické metody  
 Anonymně hostované dynamické metody jsou vytvořeny pomocí dvou <xref:System.Reflection.Emit.DynamicMethod> konstruktory, které zadejte přidruženého typu nebo modulu, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> a <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Tyto konstruktory umístěte dynamických metod poskytovaných systémem, plně důvěryhodné, transparentnost zabezpečení sestavení. Nejsou žádná oprávnění vyžaduje použití těchto konstruktorů nebo vygenerujte kód pro dynamické metody.  
  
 Místo toho když se anonymně hostovaná dynamická metoda, jsou zachyceny zásobníku volání. Když je metoda, požadavky na zabezpečení se provádí na zachycených volání zásobníku.  
  
> [!NOTE]
>  Požadavky jsou koncepčně provedené během procesu vytváření metody. To znamená požadavky se může provést podle jednotlivých instrukce jazyka MSIL je vygenerován. V aktuální implementaci jsou všechny požadavky provedené při <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> metoda je volána, nebo když je vyvolán kompilátor just-in-time (JIT), pokud je metoda vyvolána bez volání <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Pokud doména aplikace to umožňuje, můžou anonymně hostované dynamické metody přeskočí kontroly viditelnosti JIT, vztahují následující omezení: Neveřejné typy a členy přistupuje anonymně hostovaná dynamická metoda musí být v sestaveních jehož sady jsou stejné pro udělení nebo podmnožiny sady udělení generování zásobníku volání. Tuto omezenou schopnost přeskočit test viditelnosti JIT kontroluje, je povoleno, pokud doména aplikace uděluje <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak.  
  
- Pokud vaše metoda používá pouze veřejné typy a členy, během konstrukce nejsou požadována žádná oprávnění.  
  
- Pokud chcete zadat, že kontroly viditelnosti JIT přeskočen, požadavek, který je proveden, jakmile je vytvořena metoda obsahuje <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak a udělená sada oprávnění sestavení, které obsahuje neveřejný člen, která se právě využívají.  
  
 Protože je udělená množina neveřejný člen se bere v úvahu, částečně důvěryhodný kód, který bylo uděleno <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> spuštěním neveřejné členy důvěryhodných sestavení nelze zvýšit jeho oprávnění.  
  
 Jako další emitovaný kód, spouštění dynamická metoda vyžaduje oprávnění jsou vyžadována metody, které používá dynamickou metodu.  
  
 Používá systém sestavení, který je hostitelem anonymně hostované dynamické metody <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> model transparentnosti, což je model transparentnosti, která byla použita v rozhraní .NET Framework před rozhraní .NET Framework 4.  
  
 Další informace najdete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generuje se anonymně hostovaných dynamických metod z částečně důvěryhodného kódu  
 Vezměte v úvahu podmínky, ve kterých sestavení s oprávněními Internet generovat anonymně hostovaná dynamická metoda a spusťte ho:  
  
- Dynamická metoda používá pouze veřejné typy a členy. Pokud obsahuje jeho udělené sady <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, může použít neveřejné typy a členy libovolné sestavení, jejichž udělení nastavit je rovno nebo podmnožinu, sady udělení emitujícího sestavení.  
  
- Oprávnění, která jsou vyžadované všechny typy a členy, které používají dynamické metody jsou součástí sady udělení částečně důvěryhodné sestavení.  
  
> [!NOTE]
>  Dynamické metody nepodporují symboly ladění.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Dynamické metody, které jsou přidružené k existující sestavení  
 Chcete-li přidružit dynamickou metodu typu nebo modulu v existující sestavení, použijte některý z <xref:System.Reflection.Emit.DynamicMethod> konstruktory, které určují přidruženého typu nebo modulu. Oprávnění, která jsou vyžadována pro volání těchto konstruktorů lišit, protože přidružení dynamickou metodu k existujícímu typu nebo modulu poskytuje dynamická metoda přístup k neveřejným typům a členům:  
  
- Dynamickou metodu, který je přidružený k typu má přístup na všechny členy tohoto typu, dokonce i privátní členy, a všechny vnitřní typy a členy v sestavení, který obsahuje přidruženého typu.  
  
- Dynamická metoda, která souvisí s modulu má přístup ke všem `internal` typů a členů (`Friend` v jazyce Visual Basic `assembly` v common language runtime metadata) v modulu.  
  
 Kromě toho můžete použít konstruktor, který určuje, že kontroluje schopnost přeskočit viditelnost JIT kompilátoru. To poskytuje přístup vaše dynamickou metodu pro všechny typy a členy ve všech sestaveních, bez ohledu na úroveň přístupu.  
  
 Oprávnění vyžadované pomocí konstruktoru, závisí na tom, kolik přístup rozhodnete poskytnout dynamickou metodu:  
  
- Pokud vaše metoda používá pouze veřejné typy a členy a přidružíte ho k vlastní typ nebo vlastní modul, nejsou požadována žádná oprávnění.  
  
- Pokud určíte, že by měl vynechány kontroly viditelnosti JIT, konstruktor požaduje <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak.  
  
- Přidružit dynamickou metodu s jiným typem, i jiný typ ve vlastním sestavení vyžaduje konstruktor <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak a <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> příznak.  
  
- Pokud přiřadíte dynamickou metodu typu nebo modulu v jiném sestavení, konstruktoru vyžaduje dvě věci: <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak a sadu sestavení, který obsahuje další modul. To znamená, vaším zásobníkem volání musí obsahovat všechna oprávnění v sadě udělení modulu cílový plus <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    >  Z důvodu zpětné kompatibility, pokud sada udělení oprávnění požadavky na cílový plus <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> selže, požadavky konstruktor <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> příznak.  
  
 I když se položky v tomto seznamu jsou popsány z hlediska sady udělení emitujícího sestavení, mějte na paměti, že požadavky se provádí na úplného zásobníku volání, včetně hranice domény aplikace.  
  
 Další informace najdete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generování dynamických metod z částečně důvěryhodného kódu  
  
> [!NOTE]
>  Doporučený postup pro generování dynamických metod z částečně důvěryhodného kódu je použití [anonymně hostované dynamické metody](#Anonymously_Hosted_Dynamic_Methods).  
  
 Vezměte v úvahu podmínky, ve kterých sestavení s oprávněními Internet generovat dynamickou metodu a spusťte ho:  
  
- Dynamická metoda, je přidružena k modulu nebo typ, který ho vytváří nebo jeho udělené sady obsahuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a je přidružen k modulu v sestavení, jejichž udělení sada je rovna nebo podmnožinu, sady udělení emitujícího sestavení.  
  
- Dynamická metoda používá pouze veřejné typy a členy. Pokud obsahuje jeho udělené sady <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a je přidružen k modulu v sestavení, jejichž udělení sada je rovna nebo podmnožinu, sady udělení emitujícího sestavení, můžete použít typy a členy označené `internal` (`Friend` v jazyce Visual Basic `assembly`v common language runtime metadata) v modulu přidružené.  
  
- Oprávnění potřebnou pro všechny typy a členy používá dynamické metody jsou součástí sady udělení částečně důvěryhodné sestavení.  
  
- Dynamická metoda není přeskočit kontroly viditelnosti JIT.  
  
> [!NOTE]
>  Dynamické metody nepodporují symboly ladění.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Informace o verzi  
 Od verze rozhraní .NET Framework 4, zásady zabezpečení pro celý počítač odstraněny a změní výchozí mechanismus pro vynucení transparentnosti zabezpečení. Zobrazit [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Počínaje [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> příznak se už nevyžaduje při generování dynamických sestavení a dynamické metody. Tento příznak je potřeba ve všech dřívějších verzích rozhraní .NET Framework.  
  
> [!NOTE]
>  <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> příznak je zahrnutá ve výchozím nastavení `FullTrust` a `LocalIntranet` sad pojmenovaných oprávnění, ale ne `Internet` sadu oprávnění. Proto v dřívějších verzích rozhraní .NET Framework, knihovnu je možné s Internetová oprávnění pouze v případě, že se provede <xref:System.Security.PermissionSet.Assert%2A> pro <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Tyto knihovny vyžadují pečlivé ověření zabezpečení, protože chyby kódování mohou mít za následek bezpečnostní díry. [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] Umožňuje kód, aby byly vypuštěny ve scénářích s částečnou důvěryhodností bez vydávání požadavků na zabezpečení, protože generování kódu není ze své podstaty Privilegovaná operace. To znamená že generovaný kód nemá více oprávnění než sestavení, která ho vytváří. To umožňuje knihovny, které emitují kód transparentní z hlediska zabezpečení a odstraňuje nutnost vyhodnocení <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, což zjednodušuje úlohu psaní zabezpečené knihovny.  
  
 Kromě toho [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] zavádí <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak pro přístup k neveřejným typům a členům z částečně důvěryhodného dynamických metod. Starší verze rozhraní .NET Framework vyžadují <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak pro dynamické metody, které přístup k neveřejným typům a členům; jde o oprávnění, které nikdy udělení částečně důvěryhodným kódem.  
  
 Nakonec [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] zavádí anonymně hostované metody.  
  
### <a name="obtaining-information-on-types-and-members"></a>Získání informací o typech a členech  
 Počínaje [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], žádná oprávnění nejsou vyžadována k získání informací o neveřejným typům a členům. Reflexe slouží k získání informací potřebných k emitování dynamické metody. Například <xref:System.Reflection.MethodInfo> objekty se používají ke generování volání metod. Starší verze rozhraní .NET Framework vyžadují <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> příznak. Další informace najdete v tématu [Security Considerations for Reflection](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení pro reflexi](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
- [Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)
