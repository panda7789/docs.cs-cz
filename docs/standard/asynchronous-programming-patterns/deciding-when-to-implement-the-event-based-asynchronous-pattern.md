---
title: Rozhodování, kdy implementovat asynchronní vzor založený na událostech
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
ms.openlocfilehash: af30f0d09ce772f20f342ec0936d0ca63f5465d7
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365725"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Rozhodování, kdy implementovat asynchronní vzor založený na událostech
Asynchronní vzor založený na událostech poskytuje základní vzor pro vystavení asynchronních chování třídy. Se zavedením tento model [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] definuje dva modely pro vystavení asynchronních chování: asynchronní vzor založený na <xref:System.IAsyncResult?displayProperty=nameWithType> rozhraní a vzor založený na událostech. Toto téma popisuje, kdy je vhodné pro vás k implementaci oba vzorky.  
  
 Další informace o asynchronním programování se <xref:System.IAsyncResult> rozhraní najdete v tématu [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
## <a name="general-principles"></a>Obecné zásady  
 Obecně platí je potřeba zveřejnit asynchronní funkcí s použitím událostí based Asynchronous Pattern kdykoli je to možné. Existují však některé požadavky, které nedokáže ověřit jako model založený na událostech. V takových případech může být nutné implementovat <xref:System.IAsyncResult> vzor kromě vzor založený na událostech.  
  
> [!NOTE]
>  Je velmi vzácný <xref:System.IAsyncResult> vzor, který má být implementována bez také implementovat vzor založený na událostech.  
  
## <a name="guidelines"></a>Pokyny  
 Následující seznam popisuje pokyny, kdy byste měli implementovat asynchronní vzor založený na událostech:  
  
-   Použití vzoru založeného na událostech jako výchozí rozhraní API k vystavení asynchronních chování pro vaši třídu.  
  
-   Nevystavujte <xref:System.IAsyncResult> vzor, pokud vaše třída se používá především v klientské aplikaci, například Windows Forms.  
  
-   Pouze vystavit <xref:System.IAsyncResult> vzorku, když je nezbytné pro splnění vašich požadavků. Například kompatibilitu s existující rozhraní API mohou vyžadovat vám umožní vystavit <xref:System.IAsyncResult> vzor.  
  
-   Nevystavujte <xref:System.IAsyncResult> vzor bez také vystavení vzor založený na událostech.  
  
-   Pokud musí vystavit <xref:System.IAsyncResult> vzorku, Uděláte to tak jako upřesňující možnosti. Například pokud generujete objekt proxy, generovat model založený na událostech ve výchozím nastavení, existuje možnost Generovat <xref:System.IAsyncResult> vzor.  
  
-   Vytvoření vaší implementace vzor založený na událostech ve vaší <xref:System.IAsyncResult> implementaci vzoru.  
  
-   Vyhněte se úniku obou vzor založený na událostech a <xref:System.IAsyncResult> vzor ve stejné třídě. Vystavení vzor založený na událostech pro "na vyšší úrovni" třídy a <xref:System.IAsyncResult> vzor na "snížit úroveň" třídy. Například porovnat na model založený na událostech <xref:System.Net.WebClient> komponentu s <xref:System.IAsyncResult> vzor na <xref:System.Web.HttpRequest> třídy.  
  
    -   Vystavení vzor založený na událostech a <xref:System.IAsyncResult> vzor na stejné třídy, pokud to vyžaduje kompatibility. Například, pokud jste už vydali rozhraní API, které používá <xref:System.IAsyncResult> vzor, je třeba zachovat <xref:System.IAsyncResult> vzoru z důvodu zpětné kompatibility.  
  
    -   Vystavení vzor založený na událostech a <xref:System.IAsyncResult> vzorku ve stejné třídě, pokud výsledný složitost modelu objektu převažuje získané výhody oddělení implementace. Je lepší vystavit obou vzory na jednu třídu než zabráníte tak vystavení vzor založený na událostech.  
  
    -   Pokud musí vystavit obou vzor založený na událostech a <xref:System.IAsyncResult> vzor na jednu třídu, použijte <xref:System.ComponentModel.EditorBrowsableAttribute> nastavena na <xref:System.ComponentModel.EditorBrowsableState.Advanced> k označení <xref:System.IAsyncResult> implementaci vzoru jako o pokročilou funkci. Tím je oznámeno prostředí, návrh, jako je IntelliSense ve Visual Studio, ne pro zobrazení <xref:System.IAsyncResult> vlastnosti a metody. Tyto vlastnosti a metody jsou stále plně použitelné, ale vývojáři, kteří pracují pomocí IntelliSense má srozumitelnější zobrazení rozhraní API.  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Kritéria pro zveřejnění vzor IAsyncResult kromě vzor založený na událostech  
 Během asynchronního vzoru založeného na událostech má mnoho výhod podle výše uvedených scénářů, má některé nevýhody, které byste měli vědět, pokud je výkon vašich nejdůležitějších požadavek.  
  
 Existují tři scénáře, které model založený na událostech neřeší i na <xref:System.IAsyncResult> vzoru:  
  
-   Blokovat čekání na jednom <xref:System.IAsyncResult>  
  
-   Blokovat čekání na mnoha <xref:System.IAsyncResult> objekty  
  
-   Dotazovat se na dokončení <xref:System.IAsyncResult>  
  
 Tyto scénáře můžete řešit pomocí vzoru založeného na událostech, ale to je náročnější než při použití <xref:System.IAsyncResult> vzor.  
  
 Vývojáři často používají <xref:System.IAsyncResult> modelu pro služby, které mají obvykle velmi vysoký výkon požadavky. Například dotazování pro dokončení scénář je technika výkonné serveru.  
  
 Kromě toho je méně efektivní než vzor založený na událostech <xref:System.IAsyncResult> vzorek, protože vytváří více objektů, zejména <xref:System.EventArgs>, a protože synchronizuje přes více vláken.  
  
 Následující seznam uvádí několik doporučení, které řídí, pokud se rozhodnete použít <xref:System.IAsyncResult> vzoru:  
  
-   Pouze vystavit <xref:System.IAsyncResult> vzor, pokud výslovně nepotřebujete podporu <xref:System.Threading.WaitHandle> nebo <xref:System.IAsyncResult> objekty.  
  
-   Pouze vystavit <xref:System.IAsyncResult> vzor, pokud máte existující rozhraní API, které používá <xref:System.IAsyncResult> vzor.  
  
-   Pokud máte existující rozhraní API na základě <xref:System.IAsyncResult> vzorku, zvažte také zveřejnění vzor založený na událostech v další vydané verzi.  
  
-   Pouze vystavit <xref:System.IAsyncResult> vzor, pokud mají požadavky na vysoký výkon, které si ověříte nelze splnit třídou vzor založený na událostech, ale mohou být splněny <xref:System.IAsyncResult> vzor.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
