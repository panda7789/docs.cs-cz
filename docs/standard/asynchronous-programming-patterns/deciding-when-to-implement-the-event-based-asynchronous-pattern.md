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
ms.openlocfilehash: 5fca32953af91184fe99d8ef6afe5a2374f325d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663715"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Rozhodování, kdy implementovat asynchronní vzor založený na událostech

Asynchronní vzor založený na událostech poskytuje vzor pro vystavení asynchronníchování třídy. Se zavedením tohoto vzoru rozhraní .NET Framework definuje dva vzory pro vystavení asynchronní chování: asynchronní vzor na základě <xref:System.IAsyncResult?displayProperty=nameWithType> rozhraní a vzor založený na událostech. Toto téma popisuje, kdy je vhodné implementovat oba vzory.

Další informace o asynchronním programování <xref:System.IAsyncResult> s rozhraním naleznete [v tématu Asynchronní programovací model (APM).](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)

## <a name="general-principles"></a>Obecné zásady

Obecně byste měli vystavit asynchronní funkce pomocí asynchronní ho vzor založený na událostech, kdykoli je to možné. Existují však některé požadavky, které vzor založený na událostech nemůže splnit. V těchto případech může být <xref:System.IAsyncResult> nutné implementovat vzor kromě vzoru založeného na událostech.

> [!NOTE]
> Je vzácné pro <xref:System.IAsyncResult> vzor, který má být implementován bez vzor založený na událostech také implementována.

## <a name="guidelines"></a>Pokyny

Následující seznam popisuje pokyny pro, kdy byste měli implementovat asynchronní vzor založený na událostech:

- Použijte vzor založený na událostech jako výchozí rozhraní API k vystavení asynchronního chování pro vaši třídu.

- Nevystavujte <xref:System.IAsyncResult> vzor, pokud je vaše třída primárně používána v klientské aplikaci, například windows forms.

- Pouze vystavit <xref:System.IAsyncResult> vzor, pokud je to nezbytné pro splnění vašich požadavků. Například kompatibilita s existující rozhraní API <xref:System.IAsyncResult> může vyžadovat, abyste vystavit vzor.

- Nezveřejňujte <xref:System.IAsyncResult> vzorek bez vystavení vzoru založeného na událostech.

- Pokud je nutné <xref:System.IAsyncResult> vystavit vzor, uděláte to jako upřesňující možnost. Pokud například generujete objekt proxy, vygenerujte ve výchozím nastavení <xref:System.IAsyncResult> vzorek založený na událostech s možností generovat vzorek.

- Vytvořte implementaci vzoru na <xref:System.IAsyncResult> základě událostí na implementaci vzoru.

- Vyhněte se vystavení vzor založený <xref:System.IAsyncResult> na událostech a vzorek na stejné třídě. Vystavit vzor založený na událostech na "vyšší úroveň" třídy a <xref:System.IAsyncResult> vzor na "nižší úrovni" třídy. Například porovnejte vzorek založený <xref:System.Net.WebClient> na <xref:System.IAsyncResult> událostech <xref:System.Web.HttpRequest> na komponentě se vzorkem ve třídě.

  - Vystavit vzorek založený na <xref:System.IAsyncResult> událostech a vzorek na stejné třídě, když to vyžaduje kompatibilita. Například pokud jste již vydali rozhraní <xref:System.IAsyncResult> API, které používá <xref:System.IAsyncResult> vzor, budete muset zachovat vzor pro zpětnou kompatibilitu.

  - Vystavit vzor založený na <xref:System.IAsyncResult> událostech a vzor na stejné třídě, pokud složitost výsledného objektového modelu převáží výhodu oddělení implementace. Je lepší vystavit oba vzorky na jednu třídu, než aby se zabránilo vystavení vzor založený na událostech.

  - Pokud je nutné vystavit vzor založený <xref:System.IAsyncResult> na událostech a <xref:System.ComponentModel.EditorBrowsableAttribute> vzorek <xref:System.ComponentModel.EditorBrowsableState.Advanced> na <xref:System.IAsyncResult> jednu třídu, použijte sadu k označení implementace vzoru jako upřesňující funkce. To znamená, že návrh prostředí, jako je například Visual <xref:System.IAsyncResult> Studio IntelliSense, není zobrazit vlastnosti a metody. Tyto vlastnosti a metody jsou stále plně použitelné, ale vývojář pracující prostřednictvím technologie IntelliSense má jasnější zobrazení rozhraní API.

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Kritéria pro vystavení vzoru IAsyncResult kromě vzoru založeného na událostech

Zatímco asynchronní vzor založený na událostech má mnoho výhod v rámci výše uvedených scénářů, má některé nevýhody, které byste měli znát, pokud je nejdůležitější požadavek výkonu.

Existují tři scénáře, které vzor založený na událostech <xref:System.IAsyncResult> neřeší, stejně jako vzor:

- Blokování čekání na jednom<xref:System.IAsyncResult>

- Blokování čekání <xref:System.IAsyncResult> na mnoha objektech

- Dotazování na dokončení<xref:System.IAsyncResult>

Tyto scénáře můžete řešit pomocí vzoru založeného na událostech, ale <xref:System.IAsyncResult> je to více těžkopádné než použití vzoru.

Vývojáři často <xref:System.IAsyncResult> používají vzor pro služby, které mají obvykle velmi vysoké požadavky na výkon. Například dotazování pro dokončení scénář je vysoce výkonný server technika.

Vzorek založený na událostech je navíc <xref:System.IAsyncResult> méně efektivní než vzorek, <xref:System.EventArgs>protože vytváří více objektů, zejména , a protože se synchronizuje mezi vlákny.

Následující seznam ukazuje některá doporučení, která <xref:System.IAsyncResult> je třeba dodržovat, pokud se rozhodnete použít vzor:

- Pouze vystavit <xref:System.IAsyncResult> vzor, pokud konkrétně <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult> vyžadují podporu nebo objekty.

- Pouze vystavit <xref:System.IAsyncResult> vzor, pokud máte existující <xref:System.IAsyncResult> rozhraní API, které používá vzor.

- Pokud máte existující rozhraní API <xref:System.IAsyncResult> na základě vzoru, zvažte také vystavení vzor založený na událostech v další verzi.

- Pouze <xref:System.IAsyncResult> vystavit vzor, pokud máte požadavky na vysoký výkon, které jste ověřili <xref:System.IAsyncResult> nelze splnit vzor založený na událostech, ale může být splněna vzor.

## <a name="see-also"></a>Viz také

- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
