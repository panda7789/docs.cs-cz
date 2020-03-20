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
ms.openlocfilehash: 11eb4c9bc4ba1b1fe9051a04d12f893e693fb175
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180462"
---
# <a name="security-issues-in-reflection-emit"></a>Bezpečnostní problémy v generování reflexe
Rozhraní .NET Framework poskytuje tři způsoby, jak vyzařovat zprostředkující jazyk Společnosti Microsoft (MSIL), každý s vlastní problémy se zabezpečením:  
  
- [Dynamická sestavení](#Dynamic_Assemblies)  
  
- [Anonymně hostované dynamické metody](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Dynamické metody přidružené k existujícím sestavením](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Bez ohledu na způsob generování dynamického kódu vyžaduje spuštění generovaného kódu všechna oprávnění, která jsou vyžadována typy a metodami, které generovaný kód používá.  
  
> [!NOTE]
> Oprávnění, která jsou požadována pro reflexi kódu a emitující kód se změnily s následnými verzemi rozhraní .NET Framework. Viz [Informace o verzi](#Version_Information)dále v tomto tématu.  
  
<a name="Dynamic_Assemblies"></a>
## <a name="dynamic-assemblies"></a>Dynamická sestavení  
 Dynamická sestavení jsou vytvořena pomocí <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> přetížení metody. Většina přetížení této metody jsou zastaralé v rozhraní .NET Framework 4, z důvodu odstranění zásadzabezpečení celého počítače. (Viz [Změny zabezpečení](../security/security-changes.md).) Zbývající přetížení může být provedeno libovolným kódem, bez ohledu na úroveň důvěryhodnosti. Tato přetížení spadají do dvou skupin: ty, které určují seznam atributů, které mají být aplikovány na dynamické sestavení při jeho vytvoření, a ty, které ne. Pokud nezadáte model průhlednosti pro sestavu, <xref:System.Security.SecurityRulesAttribute> použijete-li atribut při jeho vytvoření, bude model průhlednosti zděděn ze sestavy emitujících.  
  
> [!NOTE]
> Atributy, které použijete na dynamické sestavení po <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> jeho vytvoření, pomocí metody se neprojeví, dokud nebude sestavení uloženo na disk a znovu načteno do paměti.  
  
 Kód v dynamickém sestavení může přistupovat k viditelným typům a členům v jiných sestaveních.  
  
> [!NOTE]
> Dynamická sestavení nepoužívají <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznaky a, které umožňují dynamické metody pro přístup k neveřejným typům a členům.  
  
 Přechodná dynamická sestavení jsou vytvořena v paměti a nikdy se neukládají na disk, takže nevyžadují žádná přístupová oprávnění k souborům. Uložení dynamického sestavení <xref:System.Security.Permissions.FileIOPermission> na disk vyžaduje příslušné příznaky.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generování dynamických sestavení z částečně důvěryhodného kódu  
 Zvažte podmínky, ve kterých může sestavení s oprávněními k Internetu generovat přechodné dynamické sestavení a spustit jeho kód:  
  
- Dynamické sestavení používá pouze veřejné typy a členy jiných sestavení.  
  
- Oprávnění vyžadovaná těmito typy a členy jsou zahrnuta v grantové sadě částečně důvěryhodného sestavení.  
  
- Sestavení není uloženo na disk.  
  
- Ladicí symboly nejsou generovány. (`Internet` `LocalIntranet` a sady oprávnění neobsahují potřebná oprávnění.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>
## <a name="anonymously-hosted-dynamic-methods"></a>Anonymně hostované dynamické metody  
 Anonymně hostované dynamické metody jsou vytvořeny <xref:System.Reflection.Emit.DynamicMethod> pomocí dvou konstruktorů, které neurčují <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>přidružený typ nebo modul a <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> . Tyto konstruktory umístit dynamické metody v systému poskytované, plně důvěryhodné, transparentní zabezpečení sestavení. K použití těchto konstruktorů nebo k vyzařování kódu pro dynamické metody nejsou vyžadována žádná oprávnění.  
  
 Místo toho při vytvoření anonymně hostované dynamické metody zásobníku volání je zachycen. Při vytvoření metody jsou požadavky na zabezpečení provedeny proti zásobníku zachyceného volání.  
  
> [!NOTE]
> Koncepčně jsou požadavky kladeny při konstrukci metody. To znamená, že požadavky by mohly být provedeny jako každý msil instrukce je emitován. V aktuální implementaci jsou všechny požadavky <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> provedeny při volání metody nebo při vyvolání kompilátoru just-in-time (JIT), pokud je metoda vyvolána bez volání <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Pokud to doména aplikace umožňuje, anonymně hostované dynamické metody mohou přeskočit kontroly viditelnosti JIT, s výhradou následujícího omezení: Neveřejné typy a členy přístupné anonymně hostovanou dynamickou metodou musí být v sestaveních, jejichž sady grantů jsou rovny nebo podmnožiny grantové sady zásobníku volání emitujících. Tato omezená možnost přeskočit kontroly viditelnosti JIT <xref:System.Security.Permissions.ReflectionPermission> je <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> povolena, pokud doména aplikace uděluje s příznakem.  
  
- Pokud vaše metoda používá pouze veřejné typy a členy, jsou během výstavby vyžadována žádná oprávnění.  
  
- Pokud zadáte, že kontroly viditelnosti JIT by měly být přeskočeny, požadavek, který je vytvořen při vytvoření metody zahrnuje <xref:System.Security.Permissions.ReflectionPermission> s příznakem <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a grantovou sadou sestavení, která obsahuje neveřejný člen, který je přístupný.  
  
 Vzhledem k tomu, že je vzata v úvahu grantová <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> sada neveřejného člena, částečně důvěryhodný kód, který byl udělen, nemůže zvýšit svá oprávnění spuštěním neveřejných členů důvěryhodných sestavení.  
  
 Stejně jako u jiných vyzařovaného kódu vyžaduje provádění dynamické metody veškerá oprávnění, která jsou požadována metodami, které dynamická metoda používá.  
  
 Systémové sestavení, které je hostitelem anonymně <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> hostovaných dynamických metod, používá model transparentnosti, což je model transparentnosti, který byl použit v rozhraní .NET Framework před rozhraním .NET Framework 4.  
  
 Další informace naleznete <xref:System.Reflection.Emit.DynamicMethod> ve třídě.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generování anonymně hostovaných dynamických metod z částečně důvěryhodného kódu  
 Zvažte podmínky, ve kterých může sestavení s oprávněními k Internetu generovat anonymně hostovanou dynamickou metodu a spustit ji:  
  
- Dynamická metoda používá pouze veřejné typy a členy. Pokud jeho grantová sada zahrnuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, může použít neveřejné typy a členy libovolného sestavení, jehož grantová sada se rovná nebo podmnožinu grantové sady sestavení emitujícího.  
  
- Oprávnění, která jsou vyžadována všemi typy a členy používanými dynamickou metodou, jsou zahrnuta v grantové sadě částečně důvěryhodného sestavení.  
  
> [!NOTE]
> Dynamické metody nepodporují ladicí symboly.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Dynamické metody přidružené k existujícím sestavením  
 Chcete-li přidružit dynamickou metodu k typu <xref:System.Reflection.Emit.DynamicMethod> nebo modulu v existujícím sestavení, použijte některý z konstruktorů, které určují přidružený typ nebo modul. Oprávnění, která jsou požadována k volání těchto konstruktorů, se liší, protože spojení dynamické metody s existujícím typem nebo modulem poskytuje dynamickou metodu přístup k neveřejným typům a členům:  
  
- Dynamická metoda, která je přidružena k typu, má přístup ke všem členům tohoto typu, dokonce i soukromým členům, a ke všem interním typům a členům v sestavení, které obsahuje přidružený typ.  
  
- Dynamická metoda, která je přidružena k `internal` modulu,`Friend` má přístup `assembly` ke všem typům a členům (v jazyce Visual Basic v metadatech modulu modulu s běžným jazykovým modulem).  
  
 Kromě toho můžete použít konstruktor, který určuje možnost přeskočit kontroly viditelnosti kompilátoru JIT. To poskytuje dynamickou metodu přístup ke všem typům a členům ve všech sestaveních bez ohledu na úroveň přístupu.  
  
 Oprávnění vyžádaná konstruktorem závisí na tom, kolik přístupu se rozhodnete udělit dynamickou metodu:  
  
- Pokud vaše metoda používá pouze veřejné typy a členy a přidružíte ji k vlastnímu typu nebo vlastnímu modulu, nejsou vyžadována žádná oprávnění.  
  
- Pokud zadáte, že kontroly viditelnosti JIT by měly být přeskočeny, konstruktor požaduje <xref:System.Security.Permissions.ReflectionPermission> s příznakem. <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>  
  
- Pokud přidružíte dynamickou metodu k jinému typu, <xref:System.Security.Permissions.ReflectionPermission> dokonce <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> i <xref:System.Security.Permissions.SecurityPermission> jinému <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> typu ve vlastním sestavení, konstruktor požaduje příznak a příznak.  
  
- Pokud přidružíte dynamickou metodu k typu nebo modulu <xref:System.Security.Permissions.ReflectionPermission> v <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> jiném sestavení, konstruktor vyžaduje dvě věci: s příznakem a grantovou sadou sestavení, která obsahuje další modul. To znamená, že zásobník volání musí obsahovat všechna oprávnění v <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>sadě udělení cílového modulu plus .  
  
    > [!NOTE]
    > Pro zpětnou kompatibilitu, pokud požadavek <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> na cíl grant <xref:System.Security.Permissions.SecurityPermission> set <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> plus selže, konstruktor požaduje s příznakem.  
  
 Přestože položky v tomto seznamu jsou popsány z hlediska grantové sady vyzařujícího sestavení, nezapomeňte, že požadavky jsou provedeny proti zásobníku úplné volání, včetně hranice domény aplikace.  
  
 Další informace naleznete <xref:System.Reflection.Emit.DynamicMethod> ve třídě.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generování dynamických metod z částečně důvěryhodného kódu  
  
> [!NOTE]
> Doporučeným způsobem generování dynamických metod z částečně důvěryhodného kódu je použití [anonymně hostovaných dynamických metod](#Anonymously_Hosted_Dynamic_Methods).  
  
 Zvažte podmínky, ve kterých může sestavení s oprávněními k Internetu generovat dynamickou metodu a spustit ji:  
  
- Buď dynamická metoda je přidružena k modulu nebo typu, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> který jej vyzařuje, nebo zahrnuje její grantovou sadu a je přidružena k modulu v sestavení, jehož grantová sada je rovna nebo podmnožině grantové sady sestavení emitujících.  
  
- Dynamická metoda používá pouze veřejné typy a členy. Pokud jeho grantová <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> sada obsahuje a je přidružena k modulu v sestavení, jehož grantová sada je rovna nebo podmnožině grantové sady sestavení emitujícího, může v přidruženém modulu používat typy a členy označené `internal` (v`Friend` jazyce Visual Basic v `assembly` metadatech modulu runtime v běžném jazyce).  
  
- Oprávnění vyžadovaná všemi typy a členy používanými dynamickou metodou jsou zahrnuta v grantové sadě částečně důvěryhodného sestavení.  
  
- Dynamická metoda nepřeskočí kontroly viditelnosti JIT.  
  
> [!NOTE]
> Dynamické metody nepodporují ladicí symboly.  
  
<a name="Version_Information"></a>
## <a name="version-information"></a>Informace o verzi  
 Počínaje rozhraním .NET Framework 4 je zrušena zásada zabezpečení celého počítače a transparentnost zabezpečení se stává výchozím mechanismem vynucení. Viz [Změny zabezpečení](../security/security-changes.md).  
  
 Počínaje rozhraním .NET Framework 2.0 <xref:System.Security.Permissions.ReflectionPermission> Service <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> Pack 1, s příznakem již není nutné při vyzařování dynamických sestavení a dynamických metod. Tento příznak je vyžadován ve všech předchozích verzích rozhraní .NET Framework.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermission>s <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> příznakem je ve `FullTrust` výchozím `LocalIntranet` nastavení zahrnuta v `Internet` a pojmenované sady oprávnění, ale ne v sadě oprávnění. Proto v dřívějších verzích rozhraní .NET Framework lze knihovnu použít s <xref:System.Security.PermissionSet.Assert%2A> oprávněními K Internetu pouze v případě, že provede for <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Tyto knihovny vyžadují pečlivou kontrolu zabezpečení, protože chyby kódování mohou způsobit bezpečnostní díry. Rozhraní .NET Framework 2.0 SP1 umožňuje kód vyzařovat v případě částečnédůvěryhodnosti bez vystavení jakékoli požadavky na zabezpečení, protože generování kódu není ze své podstaty privilegované operace. To znamená, že generovaný kód nemá žádná další oprávnění než sestavení, které jej vydává. To umožňuje knihovnám, které vyzařují kód <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>jako transparentní zabezpečení, a odstraňuje potřebu uplatnění , což zjednodušuje psaní zabezpečené knihovny.  
  
 Kromě toho .NET Framework 2.0 SP1 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> zavádí příznak pro přístup k neveřejné typy a členy z částečně důvěryhodné dynamické metody. Dřívější verze rozhraní .NET Framework <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> vyžadují příznak pro dynamické metody, které přistupují k neveřejným typům a členům; toto je oprávnění, které by nikdy nemělo být uděleno částečně důvěryhodnému kódu.  
  
 Nakonec rozhraní .NET Framework 2.0 SP1 zavádí anonymně hostované metody.  
  
### <a name="obtaining-information-on-types-and-members"></a>Získání informací o typech a členech  
 Počínaje rozhraním .NET Framework 2.0 nejsou k získání informací o neveřejných typech a členech vyžadována žádná oprávnění. Reflexe se používá k získání informací potřebných k vyzařování dynamických metod. Například <xref:System.Reflection.MethodInfo> objekty se používají k emitování volání metod. Starší verze rozhraní .NET <xref:System.Security.Permissions.ReflectionPermission> Framework <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> vyžadují příznak. Další informace naleznete v [tématu Důležité informace o zabezpečení pro reflexi](security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Viz také

- [Důležité informace o zabezpečení pro reflexi](security-considerations-for-reflection.md)
- [Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)
