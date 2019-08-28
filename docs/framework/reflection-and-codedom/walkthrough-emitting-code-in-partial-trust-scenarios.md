---
title: 'Návod: Vytváření kódu ve scénářích s částečnou důvěryhodností'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection emit, anonymously hosted dynamic methods
- partial trust, reflection
- partial trust, emitting dynamic methods
- reflection emit, partial trust scenarios
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: c45be261-2a9d-4c4e-9bd6-27f0931b7d25
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf244271010a7eb47a6c7b283a84c405108d803
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041469"
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>Návod: Vytváření kódu ve scénářích s částečnou důvěryhodností

Vygenerování reflexe používá stejnou sadu rozhraní API v plném nebo částečném vztahu důvěryhodnosti, ale některé funkce vyžadují zvláštní oprávnění v částečně důvěryhodném kódu. Kromě toho, vygenerování reflexe má funkci, anonymně hostované dynamické metody, která je navržena pro použití s částečnou důvěryhodností a sestaveními transparentními pro zabezpečení.

> [!NOTE]
> Před .NET Framework 3,5, vygeneruje <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> se kód vyžadovaný příznakem. Toto oprávnění je ve výchozím nastavení zahrnuté `FullTrust` v `Intranet` sadách a pojmenovaných oprávněních `Internet` , ale ne v sadě oprávnění. Proto by knihovna mohla být použita z částečné důvěryhodnosti pouze v případě, <xref:System.Security.SecurityCriticalAttribute> že má atribut a také <xref:System.Security.PermissionSet.Assert%2A> spustil metodu pro <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Tyto knihovny vyžadují pečlivou kontrolu zabezpečení, protože chyby kódování můžou vést k bezpečnostním otvorům. .NET Framework 3,5 umožňuje, aby byl kód generován ve scénářích s částečnou důvěryhodností bez nutnosti vydávat požadavky na zabezpečení, protože generování kódu není podstatou privilegované operace. To znamená, že generovaný kód nemá žádná další oprávnění, než sestavení, které ho emituje. To umožňuje, aby knihovny, které generují kód <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, byly transparentní pro zabezpečení a odebraly nutnost vyhodnotit, aby při psaní zabezpečené knihovny nevyžadovaly důkladnou kontrolu zabezpečení.

Tento návod znázorňuje následující úlohy:

- [Nastavení jednoduchého izolovaného prostoru pro testování částečně důvěryhodného kódu](#Setting_up).

  > [!IMPORTANT]
  > Toto je jednoduchý způsob, jak experimentovat s kódem v částečném vztahu důvěryhodnosti. Chcete-li spustit kód, který skutečně pochází z nedůvěryhodných umístění [, přečtěte si téma How to: Spustit částečně důvěryhodný kód v izolovaném](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)prostoru (sandboxu).

- [Spouštění kódu v částečně důvěryhodných doménách aplikace](#Running_code).

- [Použití anonymně hostovaných dynamických metod k vygenerování a spuštění kódu v částečném vztahu důvěryhodnosti](#Using_methods).

Další informace o vygenerování kódu ve scénářích s částečnou důvěryhodností najdete v tématu [problémy se zabezpečením v generování](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)reflexe.

Úplný seznam kódu zobrazeného v těchto postupech najdete v [části příklad](#Example) na konci tohoto návodu.

<a name="Setting_up"></a>

## <a name="setting-up-partially-trusted-locations"></a>Nastavení částečně důvěryhodných umístění

Následující dva postupy ukazují, jak nastavit umístění, ze kterých můžete testovat kód s částečnou důvěryhodností.

- První postup ukazuje, jak vytvořit doménu aplikace v izolovaném prostoru, ve kterém je kód udělena přístupová oprávnění k Internetu.

- Druhý postup ukazuje, jak přidat <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> s příznakem do domény částečně důvěryhodné aplikace, aby bylo možné povolit přístup k soukromým datům v sestaveních se stejnou nebo menší důvěryhodností.

### <a name="creating-sandboxed-application-domains"></a>Vytváření domén aplikací v izolovaném prostoru

Chcete-li vytvořit doménu aplikace, ve které jsou sestavení spouštěna s částečným vztahem důvěryhodnosti, je nutné zadat sadu oprávnění, která mají být udělena <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> sestavení pomocí přetížení metody k vytvoření domény aplikace. Nejjednodušší způsob, jak zadat sadu udělení, je načíst pojmenovanou sadu oprávnění ze zásad zabezpečení.

Následující postup vytvoří doménu aplikace v izolovaném prostoru, ve které běží váš kód s částečnou důvěryhodností, na testování scénářů, ve kterých emitující kód může přistupovat pouze k veřejným členům veřejných typů. Následující postup ukazuje, jak přidat <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>, do testovacích scénářů, ve kterých emitující kód může přistupovat k NonPublic typům a členům v sestaveních, kterým jsou udělena stejná nebo menší oprávnění.

#### <a name="to-create-an-application-domain-with-partial-trust"></a>Vytvoření domény aplikace s částečnou důvěryhodností

1. Vytvořte sadu oprávnění pro udělení sestavením v doméně aplikace v izolovaném prostoru. V takovém případě se použije sada oprávnění zóny Internet.

    [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
    [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]

2. <xref:System.AppDomainSetup> Vytvořte objekt pro inicializaci aplikační domény pomocí cesty aplikace.

    > [!IMPORTANT]
    > Pro zjednodušení tento příklad kódu používá aktuální složku. Chcete-li spustit kód, který skutečně pochází z Internetu, použijte samostatnou složku pro nedůvěryhodný kód, jak je popsáno [v tématu How to: Spustit částečně důvěryhodný kód v izolovaném](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)prostoru (sandboxu).

    [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
    [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]

3. Vytvořte doménu aplikace a určete informace o nastavení domény aplikace a sadu udělení pro všechna sestavení, která jsou spouštěna v doméně aplikace.

    [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
    [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]

    Poslední parametr <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody umožňuje zadat sadu sestavení, kterým chcete udělit úplný vztah důvěryhodnosti, namísto sady udělení domény aplikace. Nemusíte určovat .NET Framework sestavení, která vaše aplikace používá, protože tato sestavení jsou v globální mezipaměti sestavení (GAC). Sestavení v globální mezipaměti sestavení (GAC) jsou vždy plně důvěryhodná. Tento parametr můžete použít k určení sestavení se silným názvem, která nejsou v globální mezipaměti sestavení (GAC).

### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Přidání RestrictedMemberAccess k doménám v izolovaném prostoru

Hostitelské aplikace mohou umožňovat anonymně hostovaným dynamickým metodám přístup k soukromým datům v sestaveních, která mají úroveň důvěryhodnosti rovnou nebo nižší než úroveň důvěryhodnosti sestavení, které kód emituje. Chcete-li povolit tuto omezenou schopnost přeskočit kontroly viditelnosti JIT (just-in-time), hostitelská aplikace <xref:System.Security.Permissions.ReflectionPermission> přidá objekt <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> s příznakem (RMA) do sady udělení.

Hostitel může například udělit internetovým aplikacím přístupová oprávnění k Internetu a RMA, aby mohla Internetová aplikace vygenerovat kód, který přistupuje k soukromým datům ve vlastních sestaveních. Vzhledem k tomu, že přístup je omezen na sestavení se stejnou nebo menší důvěryhodností, Internetová aplikace nemůže přistupovat ke členům plně důvěryhodných sestavení, jako jsou .NET Framework sestavení.

> [!NOTE]
> Aby se zabránilo zvýšení oprávnění, jsou informace zásobníku pro vydávané sestavení zahrnuty při vytváření anonymně hostovaných dynamických metod. Při vyvolání metody jsou zkontrolovány informace o zásobníku. Anonymně hostovaná dynamická metoda, která je vyvolána z plně důvěryhodného kódu, je tedy stále omezena na úroveň důvěryhodnosti pro vygenerování sestavení.

#### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Vytvoření domény aplikace s částečnou důvěryhodností plus RMA

1. Vytvořte nový <xref:System.Security.Permissions.ReflectionPermission> objekt <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> s <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType> příznakem (RMA) a použijte metodu k přidání oprávnění do sady udělení.

    [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
    [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]

    <xref:System.Security.PermissionSet.AddPermission%2A> Metoda přidá oprávnění do sady udělení, pokud ještě není zahrnutá. Pokud je již oprávnění zahrnuto do sady udělení, zadané příznaky jsou přidány do stávajícího oprávnění.

    > [!NOTE]
    > RMA je funkce anonymně hostovaných dynamických metod. Když běžné dynamické metody přeskočí kontroly viditelnosti JIT, vygenerovaný kód vyžaduje úplný vztah důvěryhodnosti.

2. Vytvořte doménu aplikace a určete informace o nastavení domény aplikace a sadu udělení.

    [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
    [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]

<a name="Running_code"></a>

## <a name="running-code-in-sandboxed-application-domains"></a>Spouštění kódu v doménách aplikací v izolovaném prostoru

Následující postup vysvětluje, jak definovat třídu pomocí metod, které lze spustit v doméně aplikace, jak vytvořit instanci třídy v doméně a jak spustit její metody.

#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>Definování a spuštění metody v doméně aplikace

1. Definujte třídu, která je odvozena <xref:System.MarshalByRefObject>z. To umožňuje vytvářet instance třídy v jiných doménách aplikace a provádět volání metod napříč hranicemi aplikační domény. Třída v tomto příkladu je pojmenována `Worker`.

    [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
    [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]

2. Definujte veřejnou metodu, která obsahuje kód, který chcete spustit. V tomto příkladu kód generuje jednoduchou dynamickou metodu, vytvoří delegáta pro provedení metody a vyvolá delegáta.

    [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
    [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]

3. V hlavním programu Získejte zobrazovaný název sestavení. Tento název se používá při vytváření instancí `Worker` třídy v doméně aplikace v izolovaném prostoru.

    [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
    [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]

4. V hlavním programu vytvořte doménu aplikace izolovaného prostoru (sandbox), jak je popsáno v [prvním postupu](#Setting_up) v tomto návodu. Do `Internet` sady oprávnění není nutné přidávat žádná oprávnění, `SimpleEmitDemo` protože metoda používá pouze veřejné metody.

5. V hlavním programu vytvořte instanci `Worker` třídy v doméně aplikace v izolovaném prostoru.

    [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
    [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]

    <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Metoda vytvoří objekt v cílové doméně aplikace a vrátí proxy, který lze použít k volání vlastností a metod objektu.

    > [!NOTE]
    > Použijete-li tento kód v aplikaci Visual Studio, je nutné změnit název třídy tak, aby zahrnovala obor názvů. Ve výchozím nastavení je oborem názvů název projektu. Pokud je projekt například "PartialTrust", musí být název třídy "PartialTrust. Worker".

6. Přidejte kód pro volání `SimpleEmitDemo` metody. Volání je zařazeno napříč hranicí domény aplikace a kód je spuštěn v doméně aplikace v izolovaném prostoru.

    [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
    [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]

<a name="Using_methods"></a>

## <a name="using-anonymously-hosted-dynamic-methods"></a>Použití anonymně hostovaných dynamických metod

Anonymně hostované dynamické metody jsou přidruženy k transparentnímu sestavení poskytovanému systémem. Proto kód, který obsahuje, je transparentní. Běžné dynamické metody na druhé straně musí být přidružené k existujícímu modulu (ať už přímo určenému nebo odvozenému z přidruženého typu) a přebírat jejich úroveň zabezpečení z tohoto modulu.

> [!NOTE]
> Jediným způsobem, jak přidružit dynamickou metodu k sestavení, které poskytuje anonymní hostování, je použít konstruktory, které jsou popsány v následujícím postupu. Nemůžete explicitně zadat modul v sestavení anonymního hostování.

Běžné dynamické metody mají přístup k interním členům modulu, ke kterým jsou přidruženi, nebo k soukromým členům typu, ke kterému jsou přidruženy. Vzhledem k tomu, že anonymně hostované dynamické metody jsou izolované od jiného kódu, nemají přístup k soukromým datům. Mají však omezenou schopnost přeskočit kontroly viditelnosti JIT a získat tak přístup k soukromým datům. Tato možnost je omezena na sestavení, která mají úrovně důvěryhodnosti rovna nebo nižší než úroveň důvěryhodnosti sestavení, které kód emituje.

Aby se zabránilo zvýšení oprávnění, jsou informace zásobníku pro vydávané sestavení zahrnuty při vytváření anonymně hostovaných dynamických metod. Při vyvolání metody jsou zkontrolovány informace o zásobníku. Anonymně hostovaná dynamická metoda, která je vyvolána z plně důvěryhodného kódu, je stále omezena na úroveň důvěryhodnosti sestavení, které ji vyvolalo.

#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Použití anonymně hostovaných dynamických metod

- Vytvořte anonymně hostovanou dynamickou metodu pomocí konstruktoru, který neurčuje přidružený modul nebo typ.

  [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
  [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]

  Pokud anonymně hostovaná dynamická metoda používá pouze veřejné typy a metody, nevyžaduje přístup k omezenému členu a není nutné přeskočí kontroly viditelnosti JIT.

  K vygenerování dynamické metody nejsou potřeba žádná zvláštní oprávnění, ale generovaný kód vyžaduje oprávnění, která jsou vyžadovaná typy a metodami, které používá. Například pokud vygenerovaný kód volá metodu, která přistupuje k souboru, vyžaduje <xref:System.Security.Permissions.FileIOPermission>. Pokud úroveň vztahu důvěryhodnosti neobsahuje toto oprávnění, je vyvolána výjimka zabezpečení při spuštění generovaného kódu. Zde zobrazený kód emituje dynamickou metodu, která používá pouze <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodu. Proto lze kód spustit z částečně důvěryhodných umístění.

- Případně můžete vytvořit anonymně hostovanou dynamickou metodu s omezenou schopností přeskočit kontroly viditelnosti JIT pomocí <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> konstruktoru a zadáním `true` `restrictedSkipVisibility` parametru.

  [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
  [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]

  Omezení je, že anonymně hostovaná dynamická metoda má přístup k soukromým datům pouze v sestaveních s úrovní důvěryhodnosti, která se rovná nebo je menší než úroveň důvěryhodnosti vygenerovaného sestavení. Například pokud je dynamická metoda prováděna s důvěryhodností Internetu, může získat přístup k soukromým datům v jiných sestaveních, která jsou také vykonávána s důvěryhodností Internetu, ale nemůže získat přístup k soukromým datům .NET Framework sestavení. .NET Framework sestavení jsou nainstalována v globální mezipaměti sestavení (GAC) a jsou vždy plně důvěryhodná.

  Anonymně hostované dynamické metody mohou použít tuto omezenou schopnost přeskočit kontroly viditelnosti JIT pouze <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> v případě, že hostitelská aplikace udělí příznak. Požadavek na toto oprávnění je proveden při vyvolání metody.

  > [!NOTE]
  > Informace zásobníku volání pro vydávané sestavení jsou zahrnuty, pokud je vytvořena dynamická metoda. Proto se požadavek provede proti oprávněním vysílat sestavení namísto sestavení, které vyvolá metodu. Tím se zabrání spuštění vygenerovaného kódu se zvýšenými oprávněními.

  [Úplný příklad kódu](#Example) na konci tohoto návodu ukazuje použití a omezení přístupu ke členům s omezeným přístupem. Jeho `Worker` třída obsahuje metodu, která může vytvořit anonymně hostované dynamické metody s nebo bez omezené možnosti přeskočit kontroly viditelnosti a příklad ukazuje výsledek spuštění této metody v aplikačních doménách, které mají různé úrovně důvěryhodnosti.

  > [!NOTE]
  > Omezená schopnost přeskočit kontroly viditelnosti je funkce anonymně hostovaných dynamických metod. Když běžné dynamické metody přeskočí kontroly viditelnosti JIT, musí jim být udělen úplný vztah důvěryhodnosti.

<a name="Example"></a>

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad kódu ukazuje použití <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> příznaku k umožnění anonymně hostovaným dynamickým metodám přeskočit kontroly viditelnosti JIT, ale pouze v případě, že je cílový člen na stejné nebo nižší úrovni důvěryhodnosti než sestavení, které kód emituje.

V příkladu je definována `Worker` třída, která může být zařazena mezi hranice aplikační domény. Třída má dvě `AccessPrivateMethod` přetížení metod, které generují a spouštějí dynamické metody. První přetížení emituje dynamickou metodu, která volá soukromou `PrivateMethod` metodu `Worker` třídy, a může vygenerovat dynamickou metodu s kontrolami viditelnosti JIT nebo bez nich. Druhé přetížení emituje dynamickou metodu, která přistupuje k `internal` vlastnosti (`Friend` vlastnost <xref:System.String> v Visual Basic) třídy.

V příkladu se používá pomocná metoda pro vytvoření sady udělení omezené na `Internet` oprávnění a poté vytvoří doménu aplikace <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> pomocí přetížení metody k určení toho, že veškerý kód, který se spustí v doméně, používá tuto sadu udělení. Příklad vytvoří instanci `Worker` třídy v aplikační doméně a `AccessPrivateMethod` spustí metodu dvakrát.

- Při prvním `AccessPrivateMethod` spuštění metody se vynutily kontroly viditelnosti JIT. Dynamická metoda se při vyvolání nezdařila, protože kontroly viditelnosti JIT brání v přístupu k soukromé metodě.

- Při druhém `AccessPrivateMethod` spuštění metody se kontroly viditelnosti JIT přeskočí. Dynamická metoda je při kompilaci neúspěšná, protože `Internet` sada udělení neuděluje dostatečná oprávnění k přeskočení kontrol viditelnosti.

Tento příklad přidá <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> do sady udělení. Příklad potom vytvoří druhou doménu a určí, že veškerý kód, který se spustí v doméně, má oprávnění v nové sadě udělení. Příklad vytvoří instanci `Worker` třídy v nové aplikační doméně a provede obě přetížení `AccessPrivateMethod` metody.

- První přetížení `AccessPrivateMethod` metody je provedeno a kontroly viditelnosti JIT se přeskočí. Dynamická metoda se zkompiluje a provede úspěšně, protože sestavení, které generuje kód, je stejné jako sestavení, které obsahuje soukromou metodu. Proto se úrovně důvěryhodnosti rovnají. Pokud aplikace, která obsahuje `Worker` třídu, obsahovala několik sestavení, stejný proces by byl úspěšný pro každé z těchto sestavení, protože by všechny byly na stejné úrovni vztahu důvěryhodnosti.

- Druhé přetížení `AccessPrivateMethod` metody je provedeno a znovu se kontrolám viditelnosti JIT přeskočí. Tentokrát dynamická metoda při kompilaci dojde k chybě, protože se pokouší o přístup `internal` `FirstChar` k vlastnosti <xref:System.String> třídy. Sestavení, které obsahuje <xref:System.String> třídu, je plně důvěryhodné. Proto je na vyšší úrovni důvěryhodnosti než sestavení, které kód emituje.

Toto porovnání ukazuje, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> jak umožňuje částečně důvěryhodnému kódu přeskočit kontroly viditelnosti pro jiný částečně důvěryhodný kód bez narušení zabezpečení důvěryhodného kódu.

### <a name="code"></a>Kód

[!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
[!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

- Pokud tento příklad kódu sestavíte v aplikaci Visual Studio, je nutné změnit název třídy tak, aby zahrnoval obor názvů, když ho předáte <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> do metody. Ve výchozím nastavení je oborem názvů název projektu. Pokud je projekt například "PartialTrust", musí být název třídy "PartialTrust. Worker".

## <a name="see-also"></a>Viz také:

- [Bezpečnostní problémy v generování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)
- [Postupy: Spustit částečně důvěryhodný kód v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
