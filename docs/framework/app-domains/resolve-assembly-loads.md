---
title: "Řešení načítání sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3eb975b7ee8fdbba8435937fcb6f976d464db932
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="resolving-assembly-loads"></a>Řešení načítání sestavení
Poskytuje rozhraní .NET Framework <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost pro aplikace, které vyžadují větší kontrolu nad načítání sestavení. Při zpracování této událost, můžete aplikaci načtení sestavení do zatížení kontextu z mimo normální testování cesty vyberte který několik verzí sestavení načíst, Emitování dynamických sestavení a obnoví v něm a tak dále. Toto téma obsahuje pokyny pro zpracování <xref:System.AppDomain.AssemblyResolve> událostí.  
  
> [!NOTE]
>  Řešení načítání sestavení v kontextu pouze pro reflexi, použijte <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> událostí místo.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak funguje AssemblyResolve události  
 Když se zaregistrujete obslužnou rutinu pro <xref:System.AppDomain.AssemblyResolve> událostí, obslužná rutina je volána vždy, když modul runtime nepodaří vytvořit vazbu k sestavení podle názvu. Například může způsobit následující metody volání z uživatelského kódu <xref:System.AppDomain.AssemblyResolve> událost, která má být vyvolána:  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Přetížení metody nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metody, jejichž první argument je řetězec, který představuje zobrazovaný název sestavení načíst (tedy řetězec vrácený <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost).  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Přetížení metody nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metody, jejichž první argument je <xref:System.Reflection.AssemblyName> objekt, který identifikuje sestavení načíst.  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Přetížení metody.  
  
-   <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> Nebo <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> přetížení metody, která vytvoří instanci objektu v jiné doméně aplikace.  
  
### <a name="what-the-event-handler-does"></a>Jaké jsou obslužné rutiny události  
 Obslužná rutina pro <xref:System.AppDomain.AssemblyResolve> událostí obdrží zobrazovaný název sestavení, které má být načteno do <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> vlastnost. Pokud obslužná rutina nemůže rozpoznat název sestavení, vrátí hodnotu null (`Nothing` v jazyce Visual Basic `nullptr` v jazyce Visual C++).  
  
 Pokud obslužná rutina rozpozná název sestavení, může zatížení a vrátí sestavení, které splňuje požadavek. Následující seznam popisuje několik ukázkových scénářů.  
  
-   Pokud obslužná rutina nezná umístění verze sestavení, můžete načíst sestavení pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metody a může vrátit načíst sestavení, pokud bylo úspěšné.  
  
-   Pokud obslužná rutina má přístup k databázi sestavení uložené jako bajtové pole, je možné načíst pole bajtů pomocí jedné z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metody, které provést bajtové pole.  
  
-   Obslužná rutina může generovat dynamické sestavení a obnoví v něm.  
  
> [!NOTE]
>  Obslužná rutina musí načíst sestavení do načtení z kontextu, do kontextu zatížení nebo bez kontextu. Pokud obslužná rutina načte sestavení do kontextu pouze pro reflexi pomocí <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> pokus zatížení metody, která vyvolala <xref:System.AppDomain.AssemblyResolve> události nezdaří.  
  
 Je zodpovědností obslužné rutiny události vrátit vhodný sestavení. Obslužná rutina může analyzovat zobrazovaný název požadované sestavení předáním <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> hodnotu vlastnosti <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> konstruktor. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít obslužná rutina <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> vlastnosti k určení, zda je aktuální požadavek závislost sestavení. Tyto informace můžou pomoct identifikovat sestavení, které budou splňovat závislost.  
  
 Obslužné rutiny události může vrátit jinou verzi než verze, který byl vyžádán sestavení.  
  
 Ve většině případů je sestavení, které se vrátí obslužnou rutinou se zobrazí v kontextu zatížení, bez ohledu na to, které obslužná rutina načte ji do kontextu. Například, pokud obslužná rutina používá <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu pro načtení sestavení do kontextu zatížení z, sestavení se zobrazí v kontextu zatížení, když obslužná rutina vrátí ji. Ale v případě, že následující sestavení se zobrazí bez kontextu při obslužná rutina vrátí ji:  
  
-   Obslužná rutina načte sestavení bez kontextu.  
  
-   <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Vlastnost nemá hodnotu null.  
  
-   Žádajícího sestavení (to znamená, sestavení, které je vrácený <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> vlastnost) byl načten bez kontextu.  
  
 Informace o kontextu, najdete v článku <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> přetížení metody.  
  
 Několik verzí stejného sestavení je možné načíst do stejné domény aplikace. Tento postup se nedoporučuje, protože může vést k typu přiřazení problémů. V tématu [osvědčené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Obslužné rutiny události není čemu slouží  
 Primární pravidla pro zpracování <xref:System.AppDomain.AssemblyResolve> událostí je, že by se neměl pokoušet vrátit nepoznáváte sestavení. Když píšete obslužná rutina, byste měli vědět, které sestavení může způsobit událost, která má být vyvolána. Vaší obslužné rutiny pro ostatních sestavení by měl vrátit hodnotu null.  
  
> [!IMPORTANT]
>  Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.AppDomain.AssemblyResolve> událost se vyvolá pro satelitní sestavení. Tato změna ovlivňuje obslužnou rutinu události, který byl vytvořen pro dřívější verzi rozhraní .NET Framework, pokud obslužná rutina se pokusí přeložit všechny požadavky na zatížení v sestavení. Tato změna nemá vliv obslužné rutiny, které ignorovat sestavení nerozpoznají: mohly vrátit hodnotu null a dodržíte normální záložní mechanismy.  
  
 Při načítání sestavení, obslužné rutiny události nesmí používat žádné z <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metody, které můžou způsobit <xref:System.AppDomain.AssemblyResolve> událost, která má být vyvolané rekurzivně, protože to může vést k přetečení zásobníku. (Viz seznam uvedené výše v tomto tématu.) K tomu dojde i v případě, že zadáte zpracování výjimek pro žádost o načtení, protože žádná výjimka je vyvolána, dokud všechny obslužné rutiny událostí, aby vrátil. Proto následující kód vede k přetečení zásobníku Pokud `MyAssembly` nebyl nalezen:  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Doporučené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
