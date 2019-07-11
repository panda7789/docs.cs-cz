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
ms.openlocfilehash: f13a07be13294cc408cd381bef6eec1f9095365f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742459"
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>Návod: Vytváření kódu ve scénářích s částečnou důvěryhodností
Reflection emit používá stejné rozhraní API v plné nebo částečné důvěryhodnosti, ale některé funkce vyžadují zvláštní oprávnění v částečně důvěryhodným kódem. Navíc reflexe obsahuje funkci, anonymně hostované dynamické metody, který je určen pro použití s částečnou důvěryhodností a sestaveními transparentní pro zabezpečení.  
  
> [!NOTE]
>  Před rozhraní .NET Framework 3.5, generující kód vyžadoval <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> příznak. Toto oprávnění je ve výchozím nastavení zahrnuto `FullTrust` a `Intranet` sad pojmenovaných oprávnění, ale ne `Internet` sadu oprávnění. Proto knihovna může být použita z režimu částečné důvěryhodnosti pouze v případě, že měl <xref:System.Security.SecurityCriticalAttribute> atribut a také spustila <xref:System.Security.PermissionSet.Assert%2A> metodu pro <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Tyto knihovny vyžadují pečlivé ověření zabezpečení, protože chyby kódování mohou mít za následek bezpečnostní díry. Rozhraní .NET Framework 3.5 umožňuje emitování kódu ve scénářích s částečnou důvěryhodností bez vydávání požadavků na zabezpečení, protože generování kódu není ze své podstaty Privilegovaná operace. To znamená že generovaný kód nemá více oprávnění než sestavení, která ho vytváří. To umožňuje knihovnám, které emitují kód je transparentní pro zabezpečení a odstraňuje nutnost vyhodnocení <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, takže psaní zabezpečené knihovny nevyžaduje, aby takové důkladné přezkoumání zabezpečení.  
  
 Tento návod znázorňuje následující úlohy:  
  
- [Nastavení jednoduchého izolovaného prostoru pro testování částečně důvěryhodného kódu](#Setting_up).  
  
    > [!IMPORTANT]
    >  Toto je jednoduchý způsob, jak experimentovat s kódem v částečném vztahu důvěryhodnosti. Chcete-li spustit kód, který skutečně pochází z nedůvěryhodného umístění, přečtěte si téma [jak: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
- [Spouštění kódu v částečně důvěryhodných aplikačních doménách](#Running_code).  
  
- [Použití anonymně hostovaných dynamických metod k emitování a spouštění kódu v částečném vztahu důvěryhodnosti](#Using_methods).  
  
 Další informace o vytváření kódu ve scénářích s částečnou důvěryhodností, naleznete v tématu [bezpečnostní problémy v generování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md).  
  
 Úplný seznam všech kódu zobrazeného v těchto postupech najdete v článku [vzorový oddíl](#Example) na konci tohoto návodu.  
  
<a name="Setting_up"></a>   
## <a name="setting-up-partially-trusted-locations"></a>Nastavení částečně důvěryhodného umístění  
 Následující dva postupy ukazují, jak nastavit umístění, ze kterých můžete otestovat kód s částečnou důvěryhodností.  
  
- První procedura ukazuje, jak vytvořit doménu aplikace v izolovaném prostoru, ve kterém má kód udělena oprávnění Internet.  
  
- Druhý postup ukazuje, jak přidat <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak k doméně částečně důvěryhodné aplikace, povolíte přístup k soukromým datům v sestaveních stejné nebo nižší důvěry.  
  
### <a name="creating-sandboxed-application-domains"></a>Vytváření izolovaných aplikačních domén  
 K vytvoření domény aplikace 00Z vaše sestavení běží s částečnou důvěryhodností, musíte zadat sadu oprávnění, která má být poskytnuta sestavení s použitím <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody k vytvoření domény aplikace. Nejjednodušší způsob, jak určit sadu udělení, je pro načtení sadu pojmenovaných oprávnění od zásady zabezpečení.  
  
 Následující postup vytvoří doménu aplikace v izolovaném prostoru, na kterém běží váš kód s částečnou důvěryhodností pro otestování scénářů, ve kterých emitovaný kód může přistupovat pouze k veřejným členů veřejných typů. Následující postup ukazuje, jak přidat <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>do testování scénářů, ve kterých emitovaný kód může přistupovat neveřejným typům a členům v sestaveních, která jsou udělena stejná nebo nižší oprávnění.  
  
#### <a name="to-create-an-application-domain-with-partial-trust"></a>Vytvoření domény aplikace s částečnou důvěryhodností  
  
1. Vytvořte sadu oprávnění pro udělení sestavením v doméně aplikace v izolovaném prostoru. V takovém případě se používá sada oprávnění ze zóny Internet.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
     [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2. Vytvoření <xref:System.AppDomainSetup> objekt k inicializaci domény aplikace s cestou k aplikaci.  
  
    > [!IMPORTANT]
    >  Pro zjednodušení tento příklad kódu používá aktuální složku. Chcete-li spustit kód, který skutečně pochází z Internetu, použijte samostatnou složku pro nedůvěryhodný kód, a jak je popsáno v [jak: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
     [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3. Vytvořte doménu aplikace, zadejte informace o nastavení domény aplikace a sadě oprávnění pro všechna sestavení, které jsou spuštěny v doméně aplikace.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
     [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     Poslední parametr <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody umožňují zadat sadu sestavení, která má být udělena úplná důvěryhodnost namísto sady udělení aplikační domény. Není nutné zadat sestavení rozhraní .NET Framework, které vaše aplikace používá, protože jsou tato sestavení v globální mezipaměti sestavení. Sestavení v globální mezipaměti sestavení jsou vždy plně důvěryhodná. Tento parametr slouží k určení sestavení se silným názvem, které nejsou v globální mezipaměti sestavení.  
  
### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Přidání RestrictedMemberAccess do domén v izolovaném prostoru  
 Hostitelské aplikace mohou povolit anonymně hostované dynamické metody budou mít přístup k soukromým datům v sestaveních s úrovní důvěryhodnosti rovnou nebo nižší než úroveň důvěryhodnosti sestavení emitujícího kód. Pokud chcete povolit tuto omezenou schopnost přeskočit kontroly viditelnosti za běhu (JIT), přidá hostitelská aplikace <xref:System.Security.Permissions.ReflectionPermission> objektu <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> (RMA) do sady udělení.  
  
 Například hostitel může udělit internetovým aplikacím Internetová oprávnění plus RMA, takže Internetová aplikace může generovat kód, který přistupuje k soukromým datům v jejích vlastních sestaveních. Vzhledem k tomu, že přístup je omezen na sestavení stejné nebo nižší důvěry, nemůže Internetová aplikace přístup ke členům plně důvěryhodných sestavení jako je například sestavení rozhraní .NET Framework.  
  
> [!NOTE]
>  Pro zabránění zvýšení úrovně oprávnění, informace o zásobníku pro emitující sestavení je součástí anonymně hostované dynamické metody jsou vytvořeny. Při vyvolání metody, jsou zkontrolovány informace o zásobníku. Anonymně hostovaná dynamická metoda, která je vyvolána z plně důvěryhodného kódu je tedy stále omezena na úroveň důvěryhodnosti emitujícího sestavení.  
  
#### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Vytvoření domény aplikace s částečnou důvěryhodností plus RMA  
  
1. Vytvořte nový <xref:System.Security.Permissions.ReflectionPermission> objektu <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (RMA) a použijte <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType> metodu pro přidání do sady udělení oprávnění.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
     [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     <xref:System.Security.PermissionSet.AddPermission%2A> Metoda přidává oprávnění sadě udělení, pokud již není součástí. Pokud oprávnění je již součástí sady udělení, zadané příznaky jsou přidány do existujícího oprávnění.  
  
    > [!NOTE]
    >  RMA je funkce anonymně hostovaných dynamických metod. Když běžné dynamické metody přeskočí kontroly viditelnosti JIT, emitovaný kódu vyžaduje úplnou důvěryhodnost.  
  
2. Vytvořte doménu aplikace, zadejte informace o nastavení domény aplikace a poskytování nastavit.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
     [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
## <a name="running-code-in-sandboxed-application-domains"></a>Spouštění kódu v izolovaných aplikačních domén  
 Následující postup vysvětluje, jak definovat třídu pomocí metod, které mohou být provedeny v aplikační doméně, jak vytvořit instance třídy v doméně a jak provést její metody.  
  
#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>K definování a spouštění metody v aplikační doméně  
  
1. Definujte třídu, která je odvozena z <xref:System.MarshalByRefObject>. To vám umožní k vytvoření instance třídy v jiných doménách aplikace a provádět volání metody přes hranice aplikační domény. Třída v tomto příkladu má název `Worker`.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
     [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2. Definujte veřejnou metodu, která obsahuje kód, který chcete spustit. V tomto příkladu kód vyzařuje jednoduchou dynamickou metodu, vytvoří delegát k provádění metody a vyvolá delegát.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
     [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3. V hlavní aplikaci získejte zobrazovaný název vašeho sestavení. Tento název se používá při vytváření instance `Worker` třídy v doméně aplikace v izolovaném prostoru.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
     [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4. V hlavní aplikaci vytvořte doménu aplikace v izolovaném prostoru, podle popisu v [první postup](#Setting_up) v tomto názorném postupu. Nemusíte přidávat žádná oprávnění do `Internet` sadu oprávnění, protože `SimpleEmitDemo` metoda používá pouze veřejné metody.  
  
5. V hlavní aplikaci vytvořte instanci `Worker` třídy v doméně aplikace v izolovaném prostoru.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
     [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Metoda vytvoří objekt v cílové doméně aplikace a vrátí proxy, který slouží k volání vlastností a metod objektu.  
  
    > [!NOTE]
    >  Pokud použijete tento kód v sadě Visual Studio, musíte změnit název třídy, aby obsahoval obor názvů. Výchozí obor názvů je název projektu. Například pokud je projekt "PartialTrust", název třídy musí být "PartialTrust.Worker".  
  
6. Přidejte kód pro volání `SimpleEmitDemo` metody. Volání je Zařazováno přes hranici aplikační domény a kód je prováděn v izolované aplikační doméně.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
     [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
## <a name="using-anonymously-hosted-dynamic-methods"></a>Použití anonymně hostovaných dynamických metod  
 Anonymně hostované dynamické metody jsou spojeny s transparentním sestavení, která je k dispozici v systému. Proto je transparentní kód, který obsahují. Běžné dynamické metody, na druhé straně musíte přidružit k existujícímu modulu (ať už přímo určenému nebo odvozenému z přidruženého typu) a převzít úroveň zabezpečení z tohoto modulu.  
  
> [!NOTE]
>  Jediný způsob, jak přidružit dynamickou metodu k sestavení, které obsahuje anonymní hostování, je použití konstruktory, které jsou popsány v následujícím postupu. Modul nelze explicitně zadat v anonymně hostujícím sestavení.  
  
 Běžné dynamické metody mají přístup k vnitřním členům modulu, které jsou přidruženy, nebo soukromé členy typu, které jsou přidružené. Vzhledem k tomu, že anonymně hostované dynamické metody jsou izolovány od jiného kódu, nemají přístup k soukromým datům. Ale mají omezenou schopnost přeskočit kontroly viditelnosti JIT k získání přístupu k soukromým datům. Tato schopnost je omezena na sestavení, která mají úrovně důvěryhodnosti rovnou nebo nižší než úroveň důvěryhodnosti sestavení emitujícího kód.  
  
 Pro zabránění zvýšení úrovně oprávnění, informace o zásobníku pro emitující sestavení je součástí anonymně hostované dynamické metody jsou vytvořeny. Při vyvolání metody, jsou zkontrolovány informace o zásobníku. Anonymně hostovaná dynamická metoda, která je vyvolána z plně důvěryhodného kódu je stále omezena na úroveň důvěryhodnosti sestavení, které ji vydalo.  
  
#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Použití anonymně hostovaných dynamických metod  
  
- Vytvořte anonymně hostovanou dynamickou metodu pomocí konstruktoru, která neudává přiřazený modul nebo typ.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
     [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     Pokud anonymně hostovaná dynamická metoda používá pouze veřejné typy a metody, nevyžaduje přístup k omezeného člena a nebude muset přeskočit kontroly viditelnosti JIT.  
  
     Žádná zvláštní oprávnění nejsou vyžadována k emitování dynamické metody, ale emitovaný kód vyžaduje oprávnění, která jsou vyžadována typy a metody, které používá. Například pokud emitovaný kód volá metodu, která přistupuje k souboru, vyžaduje <xref:System.Security.Permissions.FileIOPermission>. Pokud úroveň důvěryhodnosti neobsahuje toto oprávnění, je vyvolána výjimka zabezpečení při spuštění emitovaného kódu. Kód zobrazený zde emituje dynamickou metodu, která používá jenom <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody. Proto lze kód spustit z částečně důvěryhodných umístění.  
  
- Alternativně vytvořte anonymně hostovanou dynamickou metodu s omezenou schopností přeskočit kontroly viditelnosti JIT pomocí <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> konstruktor a určení `true` pro `restrictedSkipVisibility` parametru.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
     [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     Omezení je, že k soukromým datům pouze v sestaveních s úrovní důvěryhodnosti rovnou nebo nižší než úroveň důvěryhodnosti emitujícího sestavení můžete přistupovat anonymně hostovaná dynamická metoda. Například pokud se dynamická metoda provádí s důvěryhodností Internetu, měl přístup k soukromým datům v jiných sestavení, které jsou také spuštěna s důvěryhodností Internetu, ale nemá přístup k soukromým datům sestavení rozhraní .NET Framework. Sestavení rozhraní .NET framework jsou nainstalované v globální mezipaměti sestavení a jsou vždy plně důvěryhodná.  
  
     Anonymně hostované dynamické metody mohou použít tuto omezenou schopnost přeskočit kontroly viditelnosti JIT, pouze pokud hostitelská aplikace poskytuje <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak. Při vyvolání metody je vznesen požadavek pro toto oprávnění.  
  
    > [!NOTE]
    >  Informace v zásobníku volání pro generování sestavení je součástí dynamická metoda vytvořena. Proto je vznesen požadavek proti oprávněním emitujícího sestavení místo sestavení, která volá metodu. To zabrání emitovanému kódu být prováděn se zvýšenými oprávněními.  
  
     [Příklad úplného kódu](#Example) na konci tohoto návodu ukazuje použití a limity omezeného přístupu k členům. Jeho `Worker` třída obsahuje metodu, která může vytvářet anonymně hostované dynamické metody s nebo bez omezené schopnosti Přeskakovat kontroly viditelnost a příklad ukazuje výsledek spuštění této metody v aplikačních doménách, které mají odlišné úrovně důvěryhodnosti.  
  
    > [!NOTE]
    >  Omezená schopnost mohla Přeskakovat kontroly viditelnosti je funkce anonymně hostovaných dynamických metod. Když běžné dynamické metody přeskočí kontroly viditelnosti JIT, musí jim být udělena úplná důvěryhodnost.  
  
<a name="Example"></a>   
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu ukazuje použití <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> příznak pro povolení anonymně hostovaným dynamickým metodám přeskočit kontroly viditelnosti JIT, ale jenom v případě, že cílový člen je na stejné nebo nižší úrovni důvěryhodnosti než sestavení, které kód emituje.  
  
 V příkladu je definována `Worker` třídu, která může být zařazována přes hranice aplikační domény. Třída má dvě `AccessPrivateMethod` přetížení metod, které emitují a spouštějí dynamické metody. První přetížení emituje dynamickou metodu, která volá soukromou `PrivateMethod` metodu `Worker` třídy a může emitovat dynamickou metodu s nebo bez kontroly viditelnosti JIT. Druhé přetížení emituje dynamickou metodu, která přistupuje k `internal` vlastnosti (`Friend` v jazyce Visual Basic) z <xref:System.String> třídy.  
  
 Tento příklad používá pomocnou metodu k vytvoření sady udělení omezené na `Internet` oprávnění a potom vytvoří aplikační doménu pomocí <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody k určení, že veškerý kód, který se spustí v doméně používá tuto sadu udělení. Tento příklad vytvoří instanci `Worker` třídy v doméně aplikace a spustí `AccessPrivateMethod` metoda dvakrát.  
  
- Prvním `AccessPrivateMethod` provedení metody, jsou vynuceny kontroly viditelnosti JIT. Dynamická metoda selže při vyvolání, protože kontroly viditelnosti JIT zabránit přístupu k soukromé metodě.  
  
- Při druhém volání `AccessPrivateMethod` provedení metody, jsou vynechány kontroly viditelnosti JIT. Dynamická metoda selže při kompilaci, protože `Internet` udělit sady neposkytuje dostatečná oprávnění k přeskočení kontrol viditelnosti.  
  
 Příklad přidá <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> k sadě udělení. Příklad poté vytvoří druhou doménu, určení, že veškerý kód, který se spustí v doméně jsou udělena oprávnění v nové sadě udělení. Tento příklad vytvoří instanci `Worker` třídy v nové doméně aplikace a spustí obě přetížení `AccessPrivateMethod` metoda.  
  
- První přetížení `AccessPrivateMethod` metoda je provedeno a kontroly viditelnosti JIT jsou vynechány. Dynamická metoda úspěšně zkompiluje a spustí, protože sestavení emitujícího kód je stejný jako sestavení, který obsahuje privátní metodu. Úrovně důvěryhodnosti jsou proto stejné. Pokud aplikace, který obsahuje `Worker` třída měla několik sestavení, stejný proces by uspěl pro kterékoli z těchto sestavení, protože všechna by byla na stejné úrovni důvěryhodnosti.  
  
- Druhé přetížení `AccessPrivateMethod` provedení metody a znovu kontroly viditelnosti JIT jsou vynechány. Tentokrát dynamická metoda selže při kompilaci, protože se pokusí získat přístup `internal` `FirstChar` vlastnost <xref:System.String> třídy. Sestavení obsahující <xref:System.String> třída je plně důvěryhodné. Proto je na vyšší úrovni důvěryhodnosti než sestavení, které kód emituje.  
  
 Toto srovnání ukazuje jak <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> umožňuje částečně důvěryhodnému kódu přeskočit test viditelnosti kontroluje pro jiný částečně důvěryhodný kódu bez ohrožení zabezpečení důvěryhodného kódu.  
  
### <a name="code"></a>Kód  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
 [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Pokud vytvoříte tento příklad kódu v sadě Visual Studio, musíte změnit název třídy, aby obsahoval obor názvů při předání do <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> metody. Výchozí obor názvů je název projektu. Například pokud je projekt "PartialTrust", název třídy musí být "PartialTrust.Worker".  
  
## <a name="see-also"></a>Viz také:

- [Bezpečnostní problémy v generování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)
- [Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
