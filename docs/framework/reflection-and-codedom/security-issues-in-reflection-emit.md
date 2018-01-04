---
title: "Bezpečnostní problémy v generování reflexe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2319ab244b2c2a296966692342df1f4967b85729
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-issues-in-reflection-emit"></a>Bezpečnostní problémy v generování reflexe
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje tři způsoby, jak emitování Microsoft mezilehlé jazyk MSIL, každou s vlastním problémy se zabezpečením:  
  
-   [Dynamická sestavení](#Dynamic_Assemblies)  
  
-   [Anonymně hostované dynamické metody](#Anonymously_Hosted_Dynamic_Methods)  
  
-   [Dynamické metody, které jsou přidružené k existující sestavení](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Bez ohledu na způsob generování dynamický kód spouštění generovaný kód vyžaduje všechna oprávnění, které jsou vyžadované typy a metody, které používá generovaného kódu.  
  
> [!NOTE]
>  Došlo ke změně oprávnění, které jsou požadovány pro odrážející na kód a generování kódu s úspěšné verzích [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. V tématu [informace o verzi](#Version_Information)dál v tomto tématu.  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>Dynamická sestavení  
 Dynamická sestavení se vytváří pomocí přetížení <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> metoda. Většina přetížení této metody jsou zastaralé v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], z důvodu odstranění zásady zabezpečení pro celý počítač. (Viz [změny zabezpečení](../../../docs/framework/security/security-changes.md).) Zbývající přetížení může provádět žádný kód, bez ohledu na úroveň důvěryhodnosti. Tato přetížení lze rozdělit do dvou skupin: ty, které zadat seznam atributů, které chcete použít u dynamických sestavení, když je vytvořen a ty, které nepodporují. Pokud nezadáte model transparentnosti pro sestavení, s použitím <xref:System.Security.SecurityRulesAttribute> atribut při vytváření, model transparentnosti je zděděn z generování sestavení.  
  
> [!NOTE]
>  Atributy, které používají dynamické sestavení po vytvoření pomocí <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> metoda, se projeví až sestavení je uložen na disk a znovu načten do paměti.  
  
 Kód v dynamickém sestavení může přistupovat viditelné typy a členy v ostatních sestavení.  
  
> [!NOTE]
>  Dynamická sestavení se nedoporučuje používat <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> a <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznaky, které umožňují dynamické metody pro přístup k neveřejní typy a členy.  
  
 Přechodný dynamická sestavení jsou vytvořené v paměti a nikdy uložen na disk, proto potřebují žádné přístupová oprávnění k souboru. Dynamická sestavení ukládání na disk vyžaduje <xref:System.Security.Permissions.FileIOPermission> s příslušnými příznaky.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generování dynamických sestavení z částečně důvěryhodného kódu  
 Vezměte v úvahu podmínky, ve kterých sestavení s oprávněními Internetu generovat přechodný dynamické sestavení a provést jeho kód:  
  
-   Dynamická sestavení používá pouze veřejné typy a členy ostatních sestavení.  
  
-   Oprávnění pro název tyto typy a členy jsou součástí sady udělení částečně důvěryhodné sestavení.  
  
-   Sestavení není uložen na disk.  
  
-   Ladění nejsou generované symboly. (`Internet` a `LocalIntranet` sady oprávnění nezahrnují potřebná oprávnění.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonymně hostované dynamické metody  
 Anonymně hostované dynamické metody se vytváří pomocí dvou <xref:System.Reflection.Emit.DynamicMethod> konstruktory, které neurčují modul, nebo přidružený typ <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> a <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Tyto konstruktory umístit dynamické metody poskytované systémem, plně důvěryhodný, transparentní pro zabezpečení sestavení. Je nutné použít tyto konstruktory nebo pro vydávání kód pro dynamické metody žádná oprávnění.  
  
 Místo toho když je vytvořen pomocí anonymně hostované dynamické metody, se zaznamená zásobníku volání. Když se metoda, jsou vytvářeny požadavky zabezpečení proti zásobníku zaznamenané volání.  
  
> [!NOTE]
>  Požadavky koncepčně, jsou vytvářeny během vytváření metody. Požadavky na to znamená, může být provedeny, jako jsou vydávány každé MSIL instrukcí. V aktuální implementace všechny požadavky probíhají, kdy <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> metoda je volána, nebo když je volána kompilátoru v běhu (JIT), pokud metoda je volána bez volání <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Pokud to dovoluje doménu aplikace, anonymně hostované dynamické metody můžete přeskočit kontroly viditelnost JIT, vztahují následující omezení: neveřejní typy a členy přistupují anonymně hostované dynamické metody musí být v sestavení, jejichž grant nastaví se rovná se nebo podmnožiny, udělte sadu generování zásobníku volání. Tato omezená schopnost přeskočit JIT viditelnost kontroluje je povolena, pokud doména aplikace uděluje <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak.  
  
-   Pokud vaše metoda se používá pouze veřejné typy a členy, během vytváření nejsou požadována žádná oprávnění.  
  
-   Pokud určíte, že JIT viditelnost kontroluje má vynecháno, požadavků, které se provádí, když se metoda zahrnuje <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak a udělte sadu sestavení, které obsahuje neveřejní člena, který je přistupuje.  
  
 Protože sady udělení neveřejní člena v úvahu, částečně důvěryhodného kódu, kterému byla udělena <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> nelze zvýšení jeho oprávnění tak, že spustíte neveřejní členové důvěryhodných sestavení.  
  
 Jako další emitovaného kód, provedení dynamické metody vyžaduje všechna oprávnění jsou pro název metody, které používá metodu dynamické.  
  
 Sestavení systému, který je hostitelem anonymně hostované dynamické metody používá <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> průhlednost model, který je průhlednost model, který byl použit v rozhraní .NET Framework, než [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
 Další informace najdete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generování anonymně hostované dynamické metody z částečně důvěryhodného kódu  
 Vezměte v úvahu podmínky, ve kterých můžete generovat anonymně hostované dynamické metody a provést sestavení s Internet oprávnění:  
  
-   Dynamické metoda se používá pouze veřejné typy a členy. Pokud obsahuje jeho grant sady <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, může použít neveřejní typy a členy jakékoli sestavení, jejichž grant nastavit je rovno, nebo jsou podmnožinou, udělte sadu generování sestavení.  
  
-   Oprávnění, která jsou nutná všechny typy a členy používá metodu dynamické jsou součástí sady udělení částečně důvěryhodné sestavení.  
  
> [!NOTE]
>  Dynamické metody nepodporují ladicími symboly.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Dynamické metody, které jsou přidružené k existující sestavení  
 Chcete-li přidružit dynamické metoda modul v existujícím sestavení nebo typ, použijte některou z <xref:System.Reflection.Emit.DynamicMethod> konstruktory, které určují přidružený typ nebo modul. Oprávnění, která jsou nutná k volání těchto konstruktorů měnit, protože existující typ přiřazení dynamické metody nebo modul umožňuje dynamické metoda přístup k neveřejní typy a členy:  
  
-   Dynamické metody, který je přidružený k typu má přístup u všech členů tohoto typu, i soukromé členy, a pro všechny interní typy a členy v sestavení obsahující typ přidružené.  
  
-   Dynamické metodu, která souvisí s modul má přístup ke všem `internal` typy a členy (`Friend` v jazyce Visual Basic `assembly` v běžná metadata language runtime) v modulu.  
  
 Kromě toho můžete použít konstruktor, který určuje, že možnost pro přeskočení viditelnost kontroluje JIT kompilátoru. Díky tomu dává vaše dynamické metoda přístup k všechny typy a členy ve všech sestaveních, bez ohledu na úroveň přístupu.  
  
 Oprávnění pro název konstruktoru závisí na tom, kolik přístup se rozhodnete udělit dynamické metodu:  
  
-   Pokud vaše metoda se používá pouze veřejné typy a členy a přiřaďte ji k vlastní typ nebo vlastní modul, nejsou požadována žádná oprávnění.  
  
-   Pokud určíte, že se má přeskočit JIT viditelnost kontroly, vyžaduje konstruktoru <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak.  
  
-   Pokud přidružíte dynamické metoda jiného typu, i jiný typ vlastního sestavení vyžaduje konstruktoru <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak a <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> příznak.  
  
-   Pokud přidružíte dynamické metoda modul v jiném sestavení nebo typ, konstruktoru vyžaduje dvě věci: <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak a udělte sadu sestavení, které obsahuje další modul. To znamená, zásobník volání musí obsahovat všechna oprávnění v sadě grant modulu cílový plus <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    >  Pro zpětnou kompatibilitu, pokud vyžádání pro cíl udělit sadu plus <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> selže, požadavky konstruktor <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> příznak.  
  
 I když se položky v tomto seznamu jsou popsány z hlediska sady udělení generování sestavení, mějte na paměti, že jsou vytvářeny požadavky proti zásobníku volání úplné, včetně hranic domény aplikace.  
  
 Další informace najdete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generování dynamických metod z částečně důvěryhodného kódu  
  
> [!NOTE]
>  Doporučený způsob generování dynamických metod z částečně důvěryhodného kódu se má používat [anonymně hostované dynamické metody](#Anonymously_Hosted_Dynamic_Methods).  
  
 Vezměte v úvahu podmínky, ve kterých sestavení s oprávněními Internetu generovat dynamické metoda a provést:  
  
-   Buď dynamické metoda je přidružena k modulu nebo typ, který vysílá ji, nebo jeho udělení sada obsahuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a je přidružen modulu v sestavení jejichž grant sada je rovno, nebo jsou podmnožinou, udělte sadu generování sestavení.  
  
-   Dynamické metoda se používá pouze veřejné typy a členy. Pokud obsahuje jeho grant sady <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a je přidružen modulu v sestavení jejichž grant sada je rovno, nebo jsou podmnožinou, udělte sadu generování sestavení, můžete použít, typy a členy označené `internal` (`Friend` v jazyce Visual Basic `assembly`v běžná metadata language runtime) v modulu přidružené.  
  
-   Oprávnění pro název všechny typy a členy používá metodu dynamické jsou součástí sady udělení částečně důvěryhodné sestavení.  
  
-   Dynamické metody není přeskočit JIT viditelnost kontroly.  
  
> [!NOTE]
>  Dynamické metody nepodporují ladicími symboly.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Informace o verzi  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zásady zabezpečení pro celý počítač je odstraněny a zabezpečení průhlednost změní výchozí mechanismus pro vynucení. V tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Od verze [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> příznak se už nevyžaduje při Emitování dynamických sestavení a dynamických metod. Tento příznak je vyžadována ve starších verzích [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  <xref:System.Security.Permissions.ReflectionPermission>s <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> příznak je zahrnutá ve výchozím nastavení v `FullTrust` a `LocalIntranet` nastaví oprávnění, ale ne v `Internet` sadu oprávnění. Proto v dřívějších verzích [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], knihovny lze použít s Internet oprávnění jenom v případě, že se provede <xref:System.Security.PermissionSet.Assert%2A> pro <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Tyto knihovny vyžadovat kontrolu pozor, zabezpečení, protože chyby kódování může mít za následek celistvosti. [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] Umožňuje kód pro vypuštění ve scénářích s částečnou důvěryhodností bez vydání všechny požadavky na zabezpečení, protože generování kódu není ze své podstaty privilegovaného operace. To znamená že generovaný kód má žádná další oprávnění než sestavení, který vysílá ho. To umožňuje knihovny, které emitování kódu být transparentní pro zabezpečení a eliminuje nutnost assert <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, což zjednodušuje zápisu knihovnu zabezpečení.  
  
 Kromě toho [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] zavádí <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak pro přístup k neveřejní typy a členy z částečně důvěryhodného dynamických metod. Starší verze [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vyžadují <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak pro dynamické metody, které přístup k neveřejní typy a členy; jde o oprávnění, které se nikdy udělení částečně důvěryhodným kódem.  
  
 Nakonec [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] zavádí anonymně hostované metody.  
  
### <a name="obtaining-information-on-types-and-members"></a>Získávání informací o pro typy a členy  
 Počínaje [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], je třeba získat informace o neveřejní typy a členy žádné oprávnění. Reflexe slouží k získání informací potřebných k emitování dynamických metod. Například <xref:System.Reflection.MethodInfo> objekty se používají k vydávání volání metody. Starší verze [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vyžadují <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> příznak. Další informace najdete v tématu [důležité informace o zabezpečení pro reflexi](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Viz také  
 [Důležité informace o zabezpečení pro reflexi](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)  
 [Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)
