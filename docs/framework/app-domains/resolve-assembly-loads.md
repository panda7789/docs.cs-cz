---
title: Řešení načítání sestavení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: accb06421b8a697b0ee89adab0a9dffa23cffb05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705672"
---
# <a name="resolving-assembly-loads"></a>Řešení načítání sestavení
Rozhraní .NET Framework poskytuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí pro aplikace, které vyžadují větší kontrolu nad načítání sestavení. Díky zpracování této události, může vaše aplikace načtení sestavení do zatížení kontextu z mimo normální definovaných cest výběr z několika verzí sestavení načíst, Emitování dynamických sestavení a vrátit ji a tak dále. Toto téma obsahuje pokyny pro zpracování <xref:System.AppDomain.AssemblyResolve> událostí.  
  
> [!NOTE]
>  Řešení načítání sestavení do kontextu pouze pro reflexi, použijte <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> události místo.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak funguje AssemblyResolve událostí  
 Při registraci obslužné rutiny pro <xref:System.AppDomain.AssemblyResolve> obslužná rutina události je vyvolána pokaždé, když modulu runtime se nepodařilo vytvořit vazbu sestavení podle názvu. Například může způsobit volání těchto metod z uživatelského kódu <xref:System.AppDomain.AssemblyResolve> události:  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Přetížení metody nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metody, jehož první argument je řetězec, který představuje zobrazovaný název sestavení (to znamená, řetězec vrácený funkcí <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost).  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Přetížení metody nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metody, jehož první argument je <xref:System.Reflection.AssemblyName> objekt, který identifikuje načtení sestavení.  
  
- <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Přetížení metody.  
  
- <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> Nebo <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> přetížení metody, která vytvoří instanci objektu v jiné doméně aplikace.  
  
### <a name="what-the-event-handler-does"></a>Co dělá obslužné rutiny události  
 Obslužná rutina pro <xref:System.AppDomain.AssemblyResolve> události obdrží zobrazovaný název sestavení, které mají být načteny v <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> vlastnost. Pokud obslužná rutina nedokáže rozpoznat název sestavení, vrátí hodnotu null (`Nothing` v jazyce Visual Basic `nullptr` v jazyce Visual C++).  
  
 Pokud obslužná rutina rozpozná název sestavení, můžete načíst a vrátit sestavení, která splňuje požadavek. Následující seznam popisuje několik ukázkových scénářů.  
  
- Pokud obslužná rutina zná umístění verzi sestavení, můžete načíst sestavení pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metody a může vrátit načtené sestavení, pokud je úspěšná.  
  
- Pokud obslužná rutina má přístup k databázi sestavení uložený jako pole bajtů, je načíst bajtového pole pomocí jedné z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metod, které trvat bajtové pole.  
  
- Obslužná rutina můžete generovat dynamické sestavení a vrátit zpět.  
  
> [!NOTE]
>  Obslužná rutina musí načíst sestavení do načtení z kontextu, v kontextu načtení, nebo bez kontextu. Pokud obslužná rutina načte sestavení do kontextu pouze pro reflexi pomocí <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> metody pokusí zatížení, která vyvolala <xref:System.AppDomain.AssemblyResolve> události nezdaří.  
  
 Zodpovídá za obslužné rutiny události k vrácení vhodný sestavení. Obslužná rutina může analyzovat zobrazovaný název požadované sestavení předáním <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> hodnoty vlastnosti <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> konstruktoru. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít obslužné rutiny <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> a určí, zda je aktuální požadavek závislost z jiného sestavení. Tyto informace můžou pomoci při identifikaci sestavení, které se bude splňovat závislost.  
  
 Obslužná rutina události může vrátit na jinou verzi než verze, který byl vyžádán sestavení.  
  
 Ve většině případů sestavení, který je vrácen rutinou se zobrazí v kontextu načtení, bez ohledu na to, které obslužná rutina načte ji do kontextu. Například, pokud obslužná rutina používá <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu pro načtení sestavení do kontextu načtení z, sestavení se zobrazí v kontextu načtení, když obslužná rutina vrátí jej. Ale v následujících případech sestavení se zobrazí bez kontextu při obslužná rutina vrátí jej:  
  
- Obslužná rutina načte sestavení bez kontextu.  
  
- <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Vlastnost nemá hodnotu null.  
  
- Žádost o sestavení (to znamená, sestavení, který je vrácen <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> vlastnost) byl načten bez kontextu.  
  
 Informace o kontextu, najdete v článku <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> přetížení metody.  
  
 Více verzí stejného sestavení, je možné načíst do stejné doméně aplikace. Tato praxe se nedoporučuje, protože to může vést k zadejte přiřazení problémy. Zobrazit [osvědčené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Co by měla obslužná rutina události není dělat  
 Primární pravidlo pro zpracování <xref:System.AppDomain.AssemblyResolve> událostí je, že by se neměl pokoušet vrátit sestavení nebyl rozpoznán. Při psaní obslužnou rutinu byste měli vědět, která sestavení může způsobit, že událost, která má být vyvolána. Vaše obslužná rutina musí vrátit hodnotu null pro jiná sestavení.  
  
> [!IMPORTANT]
>  Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.AppDomain.AssemblyResolve> událost se vyvolá pro satelitní sestavení. Tato změna ovlivní obslužnou rutinu události, která byla napsána pro starší verzi rozhraní .NET Framework, pokud obslužná rutina se pokusí přeložit všechny požadavky na zatížení v sestavení. Obslužné rutiny událostí, které ignorovat sestavení, které nerozpoznají nejsou touto změnou ovlivněny: Vrátí hodnotu null a nepoužijí normální mechanismy pro použití náhradní lokality.  
  
 Při načítání sestavení, obslužná rutina události nesmí používat kterýkoli z <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metod, které může způsobit, že <xref:System.AppDomain.AssemblyResolve> má být vyvolanou rekurzivně, protože to může vést k přetečení zásobníku. (Viz seznam uvedený výše v tomto tématu.) K tomu dochází, i v případě, že zadáte zpracování výjimek pro žádost o načtení, protože není vyvolána žádná výjimka, dokud se vrátili všechny obslužné rutiny událostí. Proto následující kód za následek přetečení zásobníku Pokud `MyAssembly` nebyl nalezen:  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Doporučené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
