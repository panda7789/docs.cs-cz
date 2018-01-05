---
title: "Rozhodování, kdy implementovat asynchronní vzor založený na událostech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 111aaaa86877368ccbd0c9c11a26dff47b065698
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Rozhodování, kdy implementovat asynchronní vzor založený na událostech
Asynchronní vzor založený na událostech poskytuje základní vzor pro vystavení asynchronní chování třídy. Se zavedením tohoto vzoru [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] definuje dva vzory pro vystavení asynchronní chování: asynchronní vzor na základě <xref:System.IAsyncResult?displayProperty=nameWithType> rozhraní a vzor na základě událostí. Toto téma popisuje, kdy je vhodné pro vás k implementaci obou vzory.  
  
 Další informace o asynchronní programování s <xref:System.IAsyncResult> rozhraní najdete v tématu [na základě událostí asynchronní vzor (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
## <a name="general-principles"></a>Obecné zásady  
 Obecně platí by měl vystavit asynchronní funkcí s použitím událostí based Asynchronous Pattern kdykoli je to možné. Existují však několik požadavků, které nesplňuje podmínky vzor na základě událostí. V takových případech může být nutné implementovat <xref:System.IAsyncResult> vzor kromě vzor na základě událostí.  
  
> [!NOTE]
>  Je obvyklé, aby <xref:System.IAsyncResult> vzor k implementaci bez také se implementuje vzor na základě událostí.  
  
## <a name="guidelines"></a>Pokyny  
 Následující seznam popisuje pokyny pro při měli byste implementovat asynchronní vzor na základě událostí:  
  
-   Použití vzoru založeného na událostech jako výchozí API vystavit asynchronní chování pro třídu.  
  
-   Nevystavujte <xref:System.IAsyncResult> vzor, když vaše třída se používá hlavně v aplikaci klienta, například Windows Forms.  
  
-   Pouze vystavit <xref:System.IAsyncResult> vzor, když je to nutné pro splnění požadavků. Pro kompatibilitu s existujícího rozhraní API může třeba vyžadovat, abyste vystavit <xref:System.IAsyncResult> vzor.  
  
-   Nevystavujte <xref:System.IAsyncResult> vzor bez také vystavení vzor na základě událostí.  
  
-   Pokud musí vystavit <xref:System.IAsyncResult> vzor, učinit jako upřesňující možnost. Například pokud vygenerování objekt proxy vygenerovat vzor na základě událostí ve výchozím nastavení s možností generovat <xref:System.IAsyncResult> vzor.  
  
-   Sestavení vaší implementace vzoru založeného na události váš <xref:System.IAsyncResult> vzor implementace.  
  
-   Vyhněte se vystavení obou vzor na základě událostí a <xref:System.IAsyncResult> vzor pro stejnou třídu. Vystavení vzor na základě událostí na "vyšší úroveň" třídy a <xref:System.IAsyncResult> vzor na "nižší úroveň" třídy. Například porovnat vzor na základě událostí na <xref:System.Net.WebClient> součásti s <xref:System.IAsyncResult> vzor na <xref:System.Web.HttpRequest> třídy.  
  
    -   Vystavení vzor na základě událostí a <xref:System.IAsyncResult> vzor pro stejnou třídu při kompatibility vyžaduje. Například, pokud již máte vydané rozhraní API, které používá <xref:System.IAsyncResult> vzor, museli byste zachovat <xref:System.IAsyncResult> vzor z důvodu zpětné kompatibility.  
  
    -   Vystavení vzor na základě událostí a <xref:System.IAsyncResult> vzor u stejné třídy, pokud výsledný objekt modelu složitost převáží výhodou oddělení implementace. Je lepší vystavit obou vzory u jedné třídy, než se vyhnout vystavení vzor na základě událostí.  
  
    -   Pokud musí vystavit obou vzor na základě událostí a <xref:System.IAsyncResult> vzor na jednu třídu, použijte <xref:System.ComponentModel.EditorBrowsableAttribute> nastavena na <xref:System.ComponentModel.EditorBrowsableState.Advanced> označit <xref:System.IAsyncResult> vzor implementace jako upřesňující funkce. To znamená do návrhu prostředí, jako například [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] technologii IntelliSense, není pro zobrazení <xref:System.IAsyncResult> vlastnosti a metody. Tyto vlastnosti a metody jsou stále plně použitelná, ale má vývojář pracující pomocí IntelliSense většího přehledu rozhraní API.  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Kritéria pro vystavení vzoru IAsyncResult kromě vzor založený na událostech  
 Během asynchronního vzoru založeného na událostech má mnoho výhod v rámci výše uvedené scénáře, nemá některé nevýhody, které byste měli vědět, pokud je vaše nejdůležitější požadavek na výkon.  
  
 Existují tři scénáře, které vzor na základě událostí neřeší společně s <xref:System.IAsyncResult> vzoru:  
  
-   Blokování čekání na jednom<xref:System.IAsyncResult>  
  
-   Blokování čekání na mnoho <xref:System.IAsyncResult> objekty  
  
-   Dotazování pro dokončení na<xref:System.IAsyncResult>  
  
 Tyto scénáře můžete vyřešit tak, že pomocí vzoru založeného na událostech, ale to se těžkopádnější než při použití <xref:System.IAsyncResult> vzor.  
  
 Vývojáři často používají <xref:System.IAsyncResult> vzor pro služby, které obvykle mají požadavky na velmi vysoký výkon. Například dotazování pro dokončení scénář je technika vysoce výkonné serveru.  
  
 Kromě toho je míň efektivní než vzor na základě událostí <xref:System.IAsyncResult> vzor, protože se tím vytvoří další objekty, zejména <xref:System.EventArgs>, a protože synchronizuje napříč vlákny.  
  
 Následující seznam uvádí několik doporučení, které řídí, pokud se rozhodnete použít <xref:System.IAsyncResult> vzoru:  
  
-   Pouze vystavit <xref:System.IAsyncResult> vzor, pokud požadujete konkrétně podpora <xref:System.Threading.WaitHandle> nebo <xref:System.IAsyncResult> objekty.  
  
-   Pouze vystavit <xref:System.IAsyncResult> vzor, pokud máte existující rozhraní API, které používá <xref:System.IAsyncResult> vzor.  
  
-   Pokud máte existujícího rozhraní API na základě <xref:System.IAsyncResult> vzor, zvažte také vystavení vzor na základě událostí v příštím vydání.  
  
-   Pouze vystavit <xref:System.IAsyncResult> vzor, pokud máte požadavky vysoký výkon, které jste ověřili nelze splnit vzor na základě událostí, ale můžete splnit <xref:System.IAsyncResult> vzor.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Vícevláknové programování s asynchronním vzorem založeným na událostech](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
