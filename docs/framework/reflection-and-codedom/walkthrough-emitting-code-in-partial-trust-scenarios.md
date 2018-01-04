---
title: "Návod: Vytváření kódu ve scénářích s částečnou důvěryhodností"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 835483d740b60f98c3170a590edbfbfbe970d783
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>Návod: Vytváření kódu ve scénářích s částečnou důvěryhodností
Emitování reflexe používá stejné rozhraní API nastavit v úplné nebo částečné důvěryhodnosti, ale některé funkce vyžadují speciální oprávnění v částečně důvěryhodným kódem. Kromě toho emitování reflexe má funkci anonymně hostované dynamické metody, která je určená pro použití s částečnou důvěryhodností a transparentní pro zabezpečení sestavení.  
  
> [!NOTE]
>  Před [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)], vytváření kódu vyžaduje <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> příznak. Toto oprávnění je zahrnutá ve výchozím nastavení `FullTrust` a `Intranet` nastaví oprávnění, ale ne v `Internet` sadě oprávnění. Proto knihovny může z částečnou důvěryhodností jenom Pokud má <xref:System.Security.SecurityCriticalAttribute> atribut a také provést <xref:System.Security.PermissionSet.Assert%2A> metodu pro <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Tyto knihovny vyžadovat kontrolu pozor, zabezpečení, protože chyby kódování může mít za následek celistvosti. [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Umožňuje kód pro vypuštění ve scénářích s částečnou důvěryhodností bez vydání všechny požadavky na zabezpečení, protože generování kódu není ze své podstaty privilegovaného operace. To znamená že generovaný kód má žádná další oprávnění než sestavení, který vysílá ho. To umožňuje knihovny, které emitování kód transparentní pro zabezpečení a eliminuje nutnost assert <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>tak, aby zápis knihovnu zabezpečené nevyžaduje, aby takové kontrolu důkladné zabezpečení.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   [Nastavení jednoduché izolovaného prostoru pro testování částečně důvěryhodného kódu](#Setting_up).  
  
    > [!IMPORTANT]
    >  Toto je jednoduchý způsob, jak experimentovat s kódem v částečné důvěryhodnosti. Pokud chcete spustit kód, který je ve skutečnosti pochází z nedůvěryhodných umístěních, najdete v části [postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
-   [Spuštění kódu v doménách částečně důvěryhodné aplikace](#Running_code).  
  
-   [Pomocí anonymně hostované dynamické metody pro vydávání a spouštění kódu v částečné důvěryhodnosti](#Using_methods).  
  
 Další informace o vytváření kódu ve scénářích s částečnou důvěryhodností najdete v tématu [problémy se zabezpečením v emitování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md).  
  
 Úplný seznam všech kód ukazuje tyto postupy, najdete v článku [oddílu příklad](#Example) na konci tohoto průvodce.  
  
<a name="Setting_up"></a>   
## <a name="setting-up-partially-trusted-locations"></a>Nastavení částečně důvěryhodného umístění  
 Tyto dva postupy ukazují, jak nastavit umístění, ze které můžete testovat kód s částečnou důvěryhodností.  
  
-   První postup ukazuje, jak vytvořit doménu v izolovaném prostoru aplikace, ve kterém je kód udělena oprávnění Internetu.  
  
-   Druhý postup ukazuje, jak přidat <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak do domény částečně důvěryhodné aplikace, abyste umožnili přístup k privátním data v sestaveních vztahu důvěryhodnosti, menší nebo rovno.  
  
### <a name="creating-sandboxed-application-domains"></a>Vytváření v izolovaném prostoru aplikační domény  
 Pokud chcete vytvořit doménu aplikace, ve kterém se vaše sestavení spouštět s částečnou důvěryhodností, musíte zadat sadu oprávnění lze udělit sestavení pomocí <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody pro vytvoření domény aplikace. Nejjednodušší způsob, jak určit sady udělení je načíst pojmenovanou sadu ze zásad zabezpečení oprávnění.  
  
 Následující postup vytvoří doméně v izolovaném prostoru aplikace, která používá kód s částečnou důvěryhodností k otestování scénářů, ve kterých emitovaného kód může přistupovat pouze veřejné členy veřejné typy. Následující postup ukazuje, jak přidat <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>, k otestování scénářů, ve kterých můžete přístup emitovaného kód neveřejní typy a členy v sestavení, která jsou udělena oprávnění stejné nebo dřívější.  
  
##### <a name="to-create-an-application-domain-with-partial-trust"></a>Vytvoření domény aplikace s částečnou důvěryhodností  
  
1.  Vytvořte nastavení oprávnění pro udělení sestavení v doméně aplikace v izolovaném prostoru. V takovém případě se používá sadu oprávnění zónu Internetu.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
     [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2.  Vytvoření <xref:System.AppDomainSetup> objektu k chybě při inicializaci domény aplikace se cesta k aplikaci.  
  
    > [!IMPORTANT]
    >  Pro zjednodušení tento příklad kódu používá aktuální složky. Pokud chcete spustit kód, který je ve skutečnosti pochází z Internetu, použít samostatnou složku pro nedůvěryhodné kód, a jak je popsáno v [postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
     [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3.  Vytvoření domény aplikace, zadání informací o nastavení domény aplikace a přidělit nastavení pro všechny sestavení, které jsou spouštěny v doméně aplikace.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
     [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     Poslední parametr <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody můžete určit sadu sestavení, která jsou udělena úplný vztah důvěryhodnosti, místo udělení sadu domény aplikace. Není nutné zadat [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sestavení, které vaše aplikace používá, protože jsou tato sestavení v globální mezipaměti sestavení. Sestavení v globální mezipaměti sestavení jsou vždy plně důvěryhodná. Tento parametr slouží k zadání sestavení se silným názvem, které nejsou v globální mezipaměti sestavení.  
  
### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Přidání RestrictedMemberAccess do domén v izolovaném prostoru  
 Hostování aplikací můžete povolit anonymně hostované dynamické metody tak, aby měl přístup k datům privátní v sestavení, které mají úrovně důvěryhodnosti, rovna nebo menší než úroveň důvěryhodnosti sestavení, který vysílá kód. Pokud chcete povolit tento s omezeným přístupem možnost pro přeskočení kontroly viditelnosti za běhu (JIT), přidá hostitelskou aplikaci <xref:System.Security.Permissions.ReflectionPermission> objektu s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak (vrácené položky) do sady udělení.  
  
 Pro hostitele může například udělit oprávnění Internet aplikací Internet plus vrácené položky, tak, aby internetové aplikace můžete vyvolat kód, který přistupuje k privátní data v jeho vlastní sestavení. Vzhledem k tomu, že přístup je omezen na sestavení menší nebo rovno vztahu důvěryhodnosti, internetovou aplikaci nelze například přístup ke členům plně důvěryhodných sestavení [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sestavení.  
  
> [!NOTE]
>  Pokud chcete zabránit zvýšení úrovně oprávnění, informace zásobníku pro generování. sestavení je součástí anonymně hostované dynamické metody se vytvářejí. Po vyvolání metody se kontroluje informace zásobníku. Proto je stále omezen na úroveň důvěryhodnosti generování sestavení anonymně hostované dynamické metody, která je volána z plně důvěryhodný kód.  
  
##### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Vytvoření domény aplikace s částečnou důvěryhodností plus vrácené položky  
  
1.  Vytvořte novou <xref:System.Security.Permissions.ReflectionPermission> objektu s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (vrácené položky) příznak a použít <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType> metodu pro přidání do sady udělení oprávnění.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
     [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     <xref:System.Security.PermissionSet.AddPermission%2A> Metoda přidá k udělení nastavit, pokud již není součástí oprávnění. Pokud toto oprávnění je už součástí sady udělení, zadaný příznaky jsou přidány do existující oprávnění.  
  
    > [!NOTE]
    >  Vrácené položky je funkce anonymně hostované dynamické metody. Pokud obyčejnou dynamické metody kontrolu JIT viditelnost, vyžaduje nástroj kód emitovaného úplný vztah důvěryhodnosti.  
  
2.  Vytvoření domény aplikace, zadání informací o nastavení domény aplikace a poskytnutí nastavit.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
     [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
## <a name="running-code-in-sandboxed-application-domains"></a>Spuštěním kódu v v izolovaném prostoru aplikační domény  
 Následující postup vysvětluje, jak definovat třídu pomocí metod, které mohou být provedeny v doméně aplikace, jak vytvořit instance třídy v doméně a jak provádět její metody.  
  
#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>K definování a provedení metody v doméně aplikace  
  
1.  Definice třídy, která je odvozena z <xref:System.MarshalByRefObject>. Díky tomu můžete vytvořit instance této třídy v jiných doménách aplikace a provádět volání metoda napříč hranicemi domény aplikace. Třída v tomto příkladu se nazývá `Worker`.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
     [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2.  Definujte veřejnou metodu, která obsahuje kód, který chcete spustit. V tomto příkladu kód vysílá dynamické jednoduše, vytvoří delegát pro spuštění metody a vyvolá delegáta.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
     [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3.  V hlavní aplikaci zobrazit zobrazovaný název vašeho sestavení. Tento název se používá při vytváření instance `Worker` – třída v doméně aplikace v izolovaném prostoru.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
     [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4.  V hlavní aplikaci vytvořit doménu v izolovaném prostoru aplikace, jak je popsáno v [první postup](#Setting_up) v tomto návodu. Nemáte žádné oprávnění k přidání `Internet` nastavit oprávnění, protože `SimpleEmitDemo` metoda se používá pouze veřejné metody.  
  
5.  V hlavní aplikaci, vytvořte instanci `Worker` – třída v doméně aplikace v izolovaném prostoru.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
     [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Metoda vytvoří objekt v cílové doméně aplikace a vrátí proxy server, který slouží k volání vlastnosti a metody objektu.  
  
    > [!NOTE]
    >  Pokud použijete tento kód v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], musíte změnit název třídy zahrnout obor názvů. Ve výchozím nastavení obor názvů je název projektu. Například pokud je projekt "PartialTrust", název třídy musí být "PartialTrust.Worker".  
  
6.  Přidejte kód volání `SimpleEmitDemo` metoda. Volání je zařazen přes hranice domény aplikace a kód se spustí v doméně aplikace v izolovaném prostoru.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
     [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
## <a name="using-anonymously-hosted-dynamic-methods"></a>Pomocí anonymně hostované dynamické metody  
 Anonymně hostované dynamické metody jsou přidruženy k transparentní sestavení, které poskytuje v systému. Proto je transparentní kód, který obsahují. Obyčejnou dynamické metody na druhé straně, musí být přidruženy k existující modul (ať už přímo zadat nebo odvodit z přidružených typu) a proveďte jejich úroveň zabezpečení z tohoto modulu.  
  
> [!NOTE]
>  Jediný způsob, jak přidružit sestavení, které poskytuje anonymní hostování dynamické metoda je použití konstruktory, které jsou popsány v následujícím postupu. V anonymní hostování sestavení nelze explicitně zadat modul.  
  
 Obyčejnou dynamické metody mít přístup k interní členů, které jsou přidruženy modul, nebo soukromé členy typu, které jsou přidruženy. Protože anonymně hostované dynamické metody jsou izolované od jiný kód, nemají přístup k privátním data. Ale mají s omezeným přístupem možnost pro přeskočení kontroly viditelnost JIT k získání přístupu k privátní data. Tato možnost je omezena na sestavení, které mají úrovně důvěryhodnosti, rovna nebo menší než úroveň důvěryhodnosti sestavení, který vysílá kód.  
  
 Pokud chcete zabránit zvýšení úrovně oprávnění, informace zásobníku pro generování. sestavení je součástí anonymně hostované dynamické metody se vytvářejí. Po vyvolání metody se kontroluje informace zásobníku. Anonymně hostované dynamické metody, která je volána z plně důvěryhodný kód je stále omezen na úroveň důvěryhodnosti sestavení, které vygenerované ho.  
  
#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Použít anonymně hostované dynamické metody  
  
-   Anonymně hostované dynamické metody vytvořte pomocí konstruktoru, která neurčuje přiřazen modul nebo typ.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
     [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     Pokud anonymně hostované dynamické metody používá pouze veřejné typy a metody, nevyžaduje přístup ke členu s omezeným přístupem a nemá tak, aby přeskočil JIT viditelnost kontroly.  
  
     Žádná zvláštní oprávnění jsou nezbytné pro vydávání dynamické metody, ale kód emitovaného vyžaduje oprávnění, které jsou vyžadovány typy a metody, které používá. Například pokud emitovaného kód volá metodu, která přistupuje k souboru, vyžaduje <xref:System.Security.Permissions.FileIOPermission>. Pokud úroveň důvěryhodnosti neobsahuje tato oprávnění, je vyvolána výjimka zabezpečení při spuštění emitovaného kódu. Kód zobrazí zde vysílá dynamické metody, která používá jenom <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metoda. Proto mohou být provedeny kód z částečně důvěryhodného umístění.  
  
-   Nebo můžete vytvořit pomocí anonymně hostované dynamické metody s s omezeným přístupem možnost pro přeskočení kontroly viditelnost JIT, pomocí <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> konstruktor a zadání `true` pro `restrictedSkipVisibility` parametr.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
     [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     Omezení je, že anonymně hostované dynamické metody přístup k datům privátní pouze v sestavení s úrovní důvěryhodnosti rovna nebo menší než úroveň důvěryhodnosti generování sestavení. Například pokud dynamické metoda provádí Internet vztahu důvěryhodnosti, má přístup k privátní data v jiných sestavení, které jsou také provádění Internet vztahu důvěryhodnosti, ale nemá přístup k privátním data [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sestavení. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]sestavení jsou nainstalované v globální mezipaměti sestavení a vždy plně důvěryhodná.  
  
     Anonymně hostované dynamické metody můžete použít s omezeným přístupem možnost pro přeskočení kontroly viditelnost JIT pouze v případě, že uděluje hostitelskou aplikaci <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak. Požadavek pro toto oprávnění je vytvořen při vyvolání metody.  
  
    > [!NOTE]
    >  Informace v zásobníku volání pro generování sestavení se při dynamické metoda je vytvořený. Proto je požadována proti oprávnění generování sestavení místo sestavení, která volá metodu. To brání tomu, aby kód emitovaného vykonáván se zvýšenými oprávněními.  
  
     [Úplný příklad kódu](#Example) na konci tento návod ukazuje použití a omezení přístup ke členu s omezeným přístupem. Jeho `Worker` třída obsahuje metody, která můžete vytvořit anonymně hostované dynamické metody s nebo bez s omezeným přístupem možnost pro přeskočení kontroly viditelnost a příklad ukazuje výsledek provedení tuto metodu v doménách aplikace, které mají různé úrovně důvěryhodnosti.  
  
    > [!NOTE]
    >  S omezeným přístupem možnost pro přeskočení kontroly viditelnost je funkce anonymně hostované dynamické metody. Když obyčejnou dynamické metody kontrolu JIT viditelnost, se musí mít udělen úplný vztah důvěryhodnosti.  
  
<a name="Example"></a>   
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu ukazuje použití <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> příznak povolit anonymně hostované dynamické metody pro přeskočení kontroly viditelnost JIT, ale jenom v případě, že je cílový člen na stejné nebo nižší úrovně důvěryhodnosti než sestavení, který vysílá kód.  
  
 V příkladu je definován `Worker` třídu, která může být zařazeno napříč hranicemi domény aplikace. Třída má dva `AccessPrivateMethod` přetížení metody, které emitování a provádění dynamických metod. První přetížení vysílá dynamické metodu, která volá privátní `PrivateMethod` metodu `Worker` třídy ale můžete Emitování dynamických metoda s nebo bez kontroly viditelnost JIT. Druhý přetížení vysílá dynamické metodu, která přistupuje `internal` vlastnost (`Friend` vlastnost v jazyce Visual Basic) z <xref:System.String> – třída.  
  
 Příklad používá metodu helper k vytvoření grant nastavit omezená na `Internet` oprávnění a pak vytváří doménu aplikace pomocí <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody k určení, že všechny kód, který se spustí v doméně používá tato sada udělení. V příkladu se vytváří instance `Worker` třídy v doméně aplikace a spustí `AccessPrivateMethod` metoda dvakrát.  
  
-   První `AccessPrivateMethod` spuštění metody, se vynucují JIT viditelnost kontroly. Dynamické metody selže při vyvolání, protože JIT viditelnost kontroly zabránit přístupu k metodě privátní.  
  
-   Při druhém `AccessPrivateMethod` spuštění metody, jsou přeskočeny JIT viditelnost kontroly. Dynamické metody selže, když je kompilován, protože `Internet` udělit sadu neuděluje dostatečná oprávnění pro přeskočení kontroly viditelnosti.  
  
 V příkladu přidáme <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> poskytnutí nastavit. Příklad poté vytvoří druhé domény, určení, že veškerý kód spustí v doméně je udělena oprávnění v nové sady udělení. V příkladu se vytváří instance `Worker` třídy v nové doméně aplikace a provede oba přetížení `AccessPrivateMethod` metoda.  
  
-   První přetížení `AccessPrivateMethod` spuštění metody a viditelnost JIT zkontroluje se přeskočí. Dynamické metody zkompiluje a provede úspěšně, protože sestavení, který vysílá kód je stejný jako sestavení, které obsahuje soukromá metoda. Proto jsou stejné úrovně důvěryhodnosti. Pokud aplikace, který obsahuje `Worker` třídy kdyby několik sestavení, stejný postup by pro každý z těchto sestavení úspěšné, protože všechny by být na stejné úrovni důvěryhodnosti.  
  
-   Druhý přetížení `AccessPrivateMethod` spuštění metody, a opakujte viditelnost JIT zkontroluje se přeskočí. Tentokrát dynamické metody selže, když je kompilován, protože se pokusí o přístup k `internal` `FirstChar` vlastnost <xref:System.String> třídy. Sestavení, které obsahuje <xref:System.String> třída je plně důvěryhodná. Proto je na vyšší úrovni vztahu důvěryhodnosti, než je sestavení, který vysílá kód.  
  
 Toto porovnání ukazuje, jak <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> umožňuje částečně důvěryhodný kód, který přeskočí viditelnost vyhledává jiný částečně důvěryhodný kód, aniž by to ohrozilo zabezpečení důvěryhodný kód.  
  
### <a name="code"></a>Kód  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
 [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Pokud vytvoříte tento příklad kódu [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], musíte změnit název třídy, které chcete zahrnout obor názvů, pokud předejte jej <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> metoda. Ve výchozím nastavení obor názvů je název projektu. Například pokud je projekt "PartialTrust", název třídy musí být "PartialTrust.Worker".  
  
## <a name="see-also"></a>Viz také  
 [Bezpečnostní problémy v generování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 [Postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
