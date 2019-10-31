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
ms.openlocfilehash: f04b40edde0755315f3b4fd4284fc7c804a54313
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130047"
---
# <a name="security-issues-in-reflection-emit"></a>Bezpečnostní problémy v generování reflexe
.NET Framework poskytuje tři způsoby, jak vygenerovat jazyk MSIL (Microsoft Intermediate Language), z nichž každá má vlastní problémy se zabezpečením:  
  
- [Dynamická sestavení](#Dynamic_Assemblies)  
  
- [Anonymně hostované dynamické metody](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Dynamické metody přidružené k existujícím sestavením](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Bez ohledu na způsob generování dynamického kódu vyžaduje spuštění vygenerovaného kódu všechna oprávnění, která jsou vyžadována typy a metodami, které vygenerovaný kód používá.  
  
> [!NOTE]
> Oprávnění, která jsou vyžadována pro reflektování kódu a vygenerování kódu, se změnila pomocí následujících vydání .NET Framework. Viz [informace o verzi](#Version_Information)dále v tomto tématu.  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>Dynamická sestavení  
 Dynamická sestavení jsou vytvořena pomocí přetížení metody <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>. Většina přetížení této metody je zastaralá v .NET Framework 4 z důvodu eliminace zásad zabezpečení na úrovni počítače. (Viz [změny zabezpečení](../security/security-changes.md).) Zbývající přetížení lze spustit libovolným kódem bez ohledu na úroveň důvěryhodnosti. Tato přetížení spadají do dvou skupin: těch, které určují seznam atributů, které mají být použity pro dynamické sestavení při jeho vytvoření, a těch, které ne. Pokud nezadáte model transparentnosti pro sestavení, při použití atributu <xref:System.Security.SecurityRulesAttribute> při jeho vytváření, je model transparentnosti zděděn z vygenerování sestavení.  
  
> [!NOTE]
> Atributy, které lze použít na dynamické sestavení po jeho vytvoření, pomocí metody <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> se neprojeví, dokud nebude sestavení uloženo na disk a znovu načteno do paměti.  
  
 Kód v dynamickém sestavení může přistupovat ke viditelným typům a členům v jiných sestaveních.  
  
> [!NOTE]
> Dynamická sestavení nepoužívají příznaky <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> a <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, které umožňují dynamickým metodám přístup k NonPublic typům a členům.  
  
 Přechodná dynamická sestavení se vytvoří v paměti a nikdy se neukládají na disk, takže nevyžadují oprávnění k přístupu k souboru. Uložení dynamického sestavení na disk vyžaduje <xref:System.Security.Permissions.FileIOPermission> s příslušnými příznaky.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generování dynamických sestavení z částečně důvěryhodného kódu  
 Vezměte v úvahu podmínky, ve kterých sestavení s oprávněními k Internetu může generovat přechodné dynamické sestavení a provést svůj kód:  
  
- Dynamické sestavení používá pouze veřejné typy a členy jiných sestavení.  
  
- Oprávnění vydaná těmito typy a členy jsou obsažena v sadě udělení částečně důvěryhodného sestavení.  
  
- Sestavení není uloženo na disk.  
  
- Symboly ladění nejsou vygenerovány. (`Internet` a `LocalIntranet` sady oprávnění nezahrnují potřebná oprávnění.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonymně hostované dynamické metody  
 Anonymně hostované dynamické metody jsou vytvářeny pomocí dvou konstruktorů <xref:System.Reflection.Emit.DynamicMethod>, které nespecifikují přidružený typ nebo modul, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> a <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Tyto konstruktory umísťují dynamické metody do plně důvěryhodného sestavení v rámci systému, které je transparentní pro zabezpečení. K použití těchto konstruktorů nebo k vygenerování kódu pro dynamické metody nejsou nutná žádná oprávnění.  
  
 Místo toho, když je vytvořena anonymně hostovaná dynamická metoda, je zachycen zásobník volání. Při konstrukci metody jsou požadavky na zabezpečení provedeny proti zachycenému zásobníku volání.  
  
> [!NOTE]
> V koncepčních případech jsou požadavky provedeny během konstrukce metody. To znamená, že požadavky mohou být provedeny při vygenerování každé instrukce jazyka MSIL. V aktuální implementaci jsou všechny požadavky provedeny, když je volána metoda <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> nebo když je vyvolána kompilátor JIT (just-in-time), pokud je metoda vyvolána bez volání <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Pokud to doména aplikace povoluje, můžou anonymně hostované dynamické metody přeskočit kontroly viditelnosti JIT, a to v souladu s následujícím omezením: typy NonPublic a členové, ke kterým přistupovala anonymně hostovaná dynamická metoda, musí být v sestaveních, jejichž sady udělení udělují. jsou rovny nebo podmnožinám, udělení sady volání zásobníku volání. Tato omezená schopnost přeskočit kontroly viditelnosti JIT je povolena, pokud aplikační doména udělí <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
- Pokud vaše metoda používá pouze veřejné typy a členy, během konstrukce nejsou požadována žádná oprávnění.  
  
- Pokud určíte, že se mají přeskočit kontroly viditelnosti JIT, požadavek, který je vytvořen při vytvoření metody, zahrnuje <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a sadou udělení sestavení, která obsahuje přistupující člena NonPublic.  
  
 Vzhledem k tomu, že se udělí sada udělení NonPublic člena, částečně důvěryhodný kód, který byl udělen <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> nemůže zvýšit oprávnění tím, že spouští NonPublic členy důvěryhodných sestavení.  
  
 Stejně jako u jakéhokoli jiného vygenerovaného kódu vyžaduje spuštění dynamické metody libovolné oprávnění metody, které používá dynamická metoda.  
  
 Systémové sestavení, které je hostitelem anonymních dynamických metod, používá <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> model transparentnosti, což je model transparentnosti, který byl použit v .NET Framework před .NET Framework 4.  
  
 Další informace naleznete v tématu Třída <xref:System.Reflection.Emit.DynamicMethod>.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generování anonymně hostovaných dynamických metod z částečně důvěryhodného kódu  
 Vezměte v úvahu podmínky, ve kterých sestavení s oprávněními k Internetu může generovat anonymně hostovanou dynamickou metodu a provést ji:  
  
- Dynamická metoda používá pouze veřejné typy a členy. Pokud jeho sada udělení zahrnuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, může použít typy NonPublic a členy všech sestavení, jejichž udělený přístup se rovná nebo je podmnožinou udělené sestavení pro generování.  
  
- Oprávnění, která jsou vyžadována všemi typy a členy použitými dynamickou metodou, jsou součástí sady udělení částečně důvěryhodného sestavení.  
  
> [!NOTE]
> Dynamické metody nepodporují symboly ladění.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Dynamické metody přidružené k existujícím sestavením  
 Chcete-li přidružit dynamickou metodu k typu nebo modulu v existujícím sestavení, použijte libovolný konstruktor <xref:System.Reflection.Emit.DynamicMethod>, který určuje přidružený typ nebo modul. Oprávnění, která jsou vyžadována pro volání těchto konstruktorů, se liší, protože přidružení dynamické metody s existujícím typem nebo modul poskytuje přístup dynamické metody k NonPublic typům a členům:  
  
- Dynamická metoda, která je přidružena k typu, má přístup ke všem členům daného typu, dokonce i k soukromým členům a všem interním typům a členům v sestavení, které obsahují přidružený typ.  
  
- Dynamická metoda, která je přidružená k modulu, má přístup ke všem typům `internal` a členům (`Friend` v Visual Basic, `assembly` v metadatech Common Language Runtime) v modulu.  
  
 Kromě toho můžete použít konstruktor, který určuje schopnost přeskočit kontroly viditelnosti kompilátoru JIT. Tím zajistíte přístup k dynamické metodě všem typům a členům ve všech sestaveních bez ohledu na úroveň přístupu.  
  
 Oprávnění, která jsou vyvolána konstruktorem závisí na tom, kolik přístupu se rozhodnete poskytnout dynamickou metodu:  
  
- Pokud vaše metoda používá pouze veřejné typy a členy a přidružíte ji k vlastnímu typu nebo vlastnímu modulu, nejsou vyžadována žádná oprávnění.  
  
- Pokud určíte, že se mají přeskočit kontroly viditelnosti JIT, konstruktor požaduje <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>.  
  
- Pokud přidružíte dynamickou metodu k jinému typu, dokonce i jiný typ ve vašem vlastním sestavení, konstruktor požaduje <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> a <xref:System.Security.Permissions.SecurityPermission> s příznakem <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType>.  
  
- Pokud přidružíte dynamickou metodu k typu nebo modulu v jiném sestavení, konstruktor požaduje dvě věci: <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a sadou udělení sestavení, která obsahuje jiný modul. To znamená, že váš zásobník volání musí zahrnovat všechna oprávnění v sadě udělení cílového modulu a navíc <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    > Z důvodu zpětné kompatibility, pokud poptávka pro cílovou sadu udělení a <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> selžou, konstruktor vyžaduje <xref:System.Security.Permissions.SecurityPermission> s příznakem <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType>.  
  
 I když jsou položky v tomto seznamu popsány v tématu udělení sady pro udělení sestavení, mějte na paměti, že požadavky jsou provedeny proti úplnému zásobníku volání, včetně hranice domény aplikace.  
  
 Další informace naleznete v tématu Třída <xref:System.Reflection.Emit.DynamicMethod>.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generování dynamických metod z částečně důvěryhodného kódu  
  
> [!NOTE]
> Doporučený způsob, jak generovat dynamické metody z částečně důvěryhodného kódu, je použití [anonymně hostovaných dynamických metod](#Anonymously_Hosted_Dynamic_Methods).  
  
 Vezměte v úvahu podmínky, ve kterých sestavení s oprávněními k Internetu může generovat dynamickou metodu a provést ji:  
  
- Buď je dynamická metoda asociována s modulem nebo typem, který ji emituje, nebo její sada udělení zahrnuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a je spojena s modulem v sestavení, jehož sada udělení je rovna nebo podmnožině, pro udělení sestavení pro generování.  
  
- Dynamická metoda používá pouze veřejné typy a členy. Pokud jeho sada udělení zahrnuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a je spojena s modulem v sestavení, jehož sada udělení je rovna nebo podmnožině, sada udělení sestavení pro generování, může použít typy a členy označené `internal` (`Friend` v Visual Basic , `assembly` v metadatech Common Language Runtime) v přidruženém modulu.  
  
- Oprávnění požadovaná všemi typy a členy, které používá dynamická metoda, jsou součástí sady udělení částečně důvěryhodného sestavení.  
  
- Dynamická metoda neskočí kontroly viditelnosti JIT.  
  
> [!NOTE]
> Dynamické metody nepodporují symboly ladění.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Informace o verzi  
 Počínaje .NET Framework 4 jsou zásady zabezpečení na úrovni počítače eliminovány a transparentnost zabezpečení se bude nacházet jako s výchozím mechanismem vynucování. Viz téma [změny zabezpečení](../security/security-changes.md).  
  
 Počínaje verzí .NET Framework 2,0 Service Pack 1 <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> již není při generování dynamických sestavení a dynamických metod vyžadován. Tento příznak je vyžadován ve všech starších verzích .NET Framework.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> je ve výchozím nastavení zahrnutá v `FullTrust` a `LocalIntranet` pojmenované sady oprávnění, ale ne v sadě oprávnění `Internet`. Proto v dřívějších verzích .NET Framework knihovna může být použita s oprávněními k Internetu pouze v případě, že spustí <xref:System.Security.PermissionSet.Assert%2A> pro <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Tyto knihovny vyžadují pečlivou kontrolu zabezpečení, protože chyby kódování můžou vést k bezpečnostním otvorům. .NET Framework 2,0 SP1 umožňuje, aby byl kód generován ve scénářích s částečnou důvěryhodností bez nutnosti vydávat požadavky na zabezpečení, protože generování kódu není podstatou privilegované operace. To znamená, že generovaný kód nemá žádná další oprávnění, než sestavení, které ho emituje. To umožňuje, aby knihovny, které generují kód, byly transparentní pro zabezpečení a odebraly nutnost vyhodnotit <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, což zjednodušuje úlohu psaní zabezpečené knihovny.  
  
 Kromě toho .NET Framework 2,0 SP1 zavádí příznak <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> pro přístup k NonPublic typům a členům z částečně důvěryhodných dynamických metod. Starší verze .NET Framework vyžadují příznak <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> pro dynamické metody, které přistupují k typům a členům NonPublic; Toto je oprávnění, které by nikdy nemělo být uděleno částečně důvěryhodnému kódu.  
  
 Nakonec .NET Framework 2,0 SP1 zavádí anonymně hostované metody.  
  
### <a name="obtaining-information-on-types-and-members"></a>Získání informací o typech a členech  
 Počínaje .NET Framework 2,0 nejsou k získání informací o typech a členech NonPublic potřeba žádná oprávnění. Reflexe se používá k získání informací potřebných k vygenerování dynamických metod. Například <xref:System.Reflection.MethodInfo> objektů slouží k vygenerování volání metody. Starší verze .NET Framework vyžadují <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType>. Další informace najdete v tématu [požadavky na zabezpečení pro reflexi](security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení pro reflexi](security-considerations-for-reflection.md)
- [Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)
