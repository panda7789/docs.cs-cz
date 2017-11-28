---
title: "Vlastnost návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 477b3b69ce1b8a3bb160e8e120885239e3d99e56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="property-design"></a>Vlastnost návrhu
I když jsou vlastnosti technicky velmi podobné metody, se výrazně lišit podle toho scénáře jejich použití. Měla by se zobrazit jako inteligentní pole. Mají volání syntaxe polí a flexibilitu metod.  
  
 **PROVEĎTE ✓** vytvořit vlastnosti jen pro get, pokud má volající neměli mít možnost ke změně hodnoty vlastnosti.  
  
 Mějte na paměti že pokud typ je typ Měnitelná odkazu vlastnost, hodnota vlastnosti lze změnit, i když je vlastnost pouze pro získání.  
  
 **X nesmí** poskytnout setter s širší usnadnění než metoda getter vlastnosti jen pro sadu nebo vlastnosti.  
  
 Například nepoužívejte vlastnosti s veřejnou metodu setter a chráněné getter.  
  
 Pokud metoda getter vlastnosti nelze zadat, implementujte funkce jako metodu. Vezměte v úvahu spouštění název metody s `Set` a postupujte podle pokynů s co jste by mít s názvem vlastnosti. Například <xref:System.AppDomain> má metodu s názvem `SetCachePath` místo nutnosti ryze sadu vlastnost s názvem `CachePath`.  
  
 **PROVEĎTE ✓** zadejte rozumný výchozí hodnoty pro všechny vlastnosti, zajistíte, že výchozí hodnoty nezpůsobovalo neustálé bezpečnostní riziko nebo terribly neefektivní kód.  
  
 **PROVEĎTE ✓** povolit vlastnosti nastavit v libovolném pořadí, i když to vede k dočasné neplatný stav objektu.  
  
 Je běžné, že dvě nebo více vlastností být vzájemně souvisejících do bodu, kde některé hodnoty jednu vlastnost může být neplatný zadané hodnotách jiných vlastností na stejný objekt. V takových případech by výjimky vzniklé v neplatném stavu posunut, dokud vzájemně souvisejících vlastnosti jsou ve skutečnosti společně použít objekt.  
  
 **PROVEĎTE ✓** zachovat předchozí hodnotu, pokud metoda setter vlastnosti vyvolá výjimku.  
  
 **X nepoužívejte** vyvolání výjimky z metody vlastnost getter.  
  
 Mechanismy získání vlastnost by měla být jednoduché operace a nesmí mít žádné předpoklady. Pokud příjemce může vyvolat výjimku, by pravděpodobně přepracovali metodu. Všimněte si, že toto pravidlo se nevztahuje na indexery, kde Očekáváme, že výjimky v důsledku ověřování argumenty.  
  
### <a name="indexed-property-design"></a>Indexované vlastnosti návrhu  
 Indexované vlastnosti je speciální vlastnost, která může mít parametry a může být volána s speciální syntaxe podobná indexu pole.  
  
 Indexované vlastnosti se běžně označují jako indexery. Indexery by měl použít pouze v rozhraní API, které poskytují přístup k položkám v logické kolekce. Například řetězec je kolekce znaky a indexeru na <xref:System.String?displayProperty=nameWithType> byl přidán k jeho znaků.  
  
 **✓ ZVAŽTE** použití indexery pro poskytnutí přístupu k datům uloženým v interní pole.  
  
 **✓ ZVAŽTE** poskytuje indexery na typy reprezentující kolekce položek.  
  
 **X nepoužívejte** použití indexovaných vlastností s více než jeden parametr.  
  
 Pokud návrh vyžaduje několik parametrů, znovu zda přistupující objekt vlastnosti skutečně představuje logické kolekce. Pokud ne, používejte metody. Vezměte v úvahu spouštění název metody s `Get` nebo `Set`.  
  
 **X nepoužívejte** indexery s typy parametrů jinak než <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, nebo výčet.  
  
 Pokud návrh vyžaduje jiné typy parametrů, důrazně přehodnocovat zda rozhraní API skutečně představuje přistupující objekt logické kolekce. Pokud ne, použijte metodu. Vezměte v úvahu spouštění název metody s `Get` nebo `Set`.  
  
 **PROVEĎTE ✓** použijte název `Item` pro indexovaných vlastností, pokud je samozřejmě lepší název (například najdete v článku <xref:System.String.Chars%2A> vlastnost na `System.String`).  
  
 V jazyce C# indexery jsou ve výchozím nastavení s názvem položky. <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Můžete použít k přizpůsobení tento název.  
  
 **X nesmí** zadejte indexer a metody, které jsou sémanticky ekvivalentní.  
  
 **X nesmí** zadat více než jednu řadu přetížené indexery jednomu typu.  
  
 Tato velikost je vyžadována kompilátorem C#.  
  
 **X nesmí** nevýchozí použití indexovaných vlastností.  
  
 Tato velikost je vyžadována kompilátorem C#.  
  
### <a name="property-change-notification-events"></a>Vlastnosti události oznámení změny  
 Někdy je užitečné k poskytování událost upozornění uživatele o změnách v hodnotě vlastnosti. Například `System.Windows.Forms.Control` vyvolá `TextChanged` události po hodnotu jeho `Text` došlo ke změně vlastností.  
  
 **✓ ZVAŽTE** vyvolání změnit události oznámení při změně hodnoty vlastností v vysoké úrovně rozhraní API (obvykle návrháře komponenty).  
  
 Pokud je dobré scénář pro uživatele vědět, když je změna vlastnost objektu, objektu by měla vyvolat událost upozornění změnu pro vlastnost.  
  
 Je však pravděpodobně být vhodné režii vyvolat takové události pro nízké úrovně rozhraní API, například základní typy nebo kolekce. Například <xref:System.Collections.Generic.List%601> nebude vyvolat tyto události při přidání nové položky do seznamu a `Count` změny vlastností.  
  
 **✓ ZVAŽTE** vyvolání události oznámení při změně hodnoty vlastnosti prostřednictvím externí vynutí změn.  
  
 Pokud se změní hodnotu vlastnosti prostřednictvím některé externí force (způsobem, jinak než pomocí volání metody u objektu), vyvolat události označují vývojář, že hodnota se mění a došlo ke změně. Dobrým příkladem je `Text` vlastností ovládacího prvku textové pole. Když uživatel zadá text v `TextBox`, hodnota vlastnosti automaticky změní.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Člen pokynů pro návrh](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)
