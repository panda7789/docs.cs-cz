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
ms.openlocfilehash: c235a838504889a105ef98df47f7373a145503da
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289444"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Rozhodování, kdy implementovat asynchronní vzor založený na událostech

Asynchronní vzor založený na událostech poskytuje vzor pro vystavení asynchronního chování třídy. Při zavedení tohoto modelu .NET Framework definuje dva vzory pro vystavení asynchronního chování: asynchronní vzor založený na <xref:System.IAsyncResult?displayProperty=nameWithType> rozhraní a vzor založený na událostech. Toto téma popisuje, kdy je vhodné implementovat oba vzory.

Další informace o asynchronním programování s <xref:System.IAsyncResult> rozhraním naleznete v tématu [Asynchronous Programming model (APM)](asynchronous-programming-model-apm.md).

## <a name="general-principles"></a>Obecné zásady

Obecně byste měli zveřejnit asynchronní funkce pomocí asynchronního vzoru založeného na událostech, kdykoli je to možné. Existují však některé požadavky, které vzor založený na událostech nedokáže splnit. V těchto případech může být nutné implementovat <xref:System.IAsyncResult> vzor kromě vzoru založeného na událostech.

> [!NOTE]
> Je zřídka pro <xref:System.IAsyncResult> implementaci modelu bez nutnosti implementace vzoru založeného na událostech.

## <a name="guidelines"></a>Pokyny

Následující seznam popisuje pokyny pro případ, kdy byste měli implementovat asynchronní vzor založený na událostech:

- Použijte vzor založený na událostech jako výchozí rozhraní API k vystavení asynchronního chování vaší třídy.

- Nezveřejňujte <xref:System.IAsyncResult> vzor, pokud je vaše třída primárně používána v klientské aplikaci, například model Windows Forms.

- Vystavte si vzor jenom v <xref:System.IAsyncResult> případě, že je to nutné pro splnění vašich požadavků. Například kompatibilita s existujícím rozhraním API může vyžadovat, abyste vystavili <xref:System.IAsyncResult> vzor.

- Nezveřejňujte <xref:System.IAsyncResult> vzor, aniž by bylo nutné vystavit vzor založený na událostech.

- Pokud je nutné vystavit <xref:System.IAsyncResult> vzor, udělejte to jako pokročilou možnost. Například Pokud vygenerujete objekt proxy, vygenerujte vzor založený na událostech ve výchozím nastavení s možností pro vygenerování <xref:System.IAsyncResult> vzoru.

- Sestavení implementace vzoru založeného na událostech pro <xref:System.IAsyncResult> implementaci vzoru.

- Vyhněte se zveřejnění vzoru založeného na událostech i <xref:System.IAsyncResult> vzoru ve stejné třídě. Vystavte vzor založený na událostech na třídách vyšší úrovně a <xref:System.IAsyncResult> vzor na třídách nižší úrovně. Například Porovnejte vzor založený na událostech na <xref:System.Net.WebClient> komponentě se <xref:System.IAsyncResult> vzorem <xref:System.Web.HttpRequest> třídy.

  - Vystavte vzor založený na událostech a <xref:System.IAsyncResult> vzor na stejné třídě, pokud to vyžaduje kompatibilita. Například pokud jste již vystavili rozhraní API, které používá <xref:System.IAsyncResult> vzor, je třeba zachovat <xref:System.IAsyncResult> vzorek pro zpětnou kompatibilitu.

  - Vystavte vzor založený na událostech a <xref:System.IAsyncResult> vzor na stejné třídě, pokud výsledná složitost objektového modelu převažuje nad výhodou oddělení implementací. Je lepší zveřejnit oba vzory pro jednu třídu, než aby se zabránilo zveřejnění vzoru založeného na událostech.

  - Pokud je nutné vystavit vzor a vzor založený na událostech <xref:System.IAsyncResult> pro jednu třídu, použijte možnost <xref:System.ComponentModel.EditorBrowsableAttribute> nastavit na <xref:System.ComponentModel.EditorBrowsableState.Advanced> k označení <xref:System.IAsyncResult> implementace vzoru jako pokročilé funkce. To označuje návrh prostředí, jako je například Visual Studio IntelliSense, nikoli zobrazení <xref:System.IAsyncResult> vlastností a metod. Tyto vlastnosti a metody jsou stále plně použitelné, ale vývojáři, kteří pracují prostřednictvím technologie IntelliSense, mají jasnou pohled na rozhraní API.

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Kritéria pro vystavení vzoru IAsyncResult kromě vzoru založeného na událostech

I když asynchronní vzor založený na událostech obsahuje mnoho výhod v rámci dřív zmíněných scénářů, má některé nevýhody, o kterých byste měli vědět, zda je výkon nejdůležitějším požadavkem.

Existují tři scénáře, které vzor založený na událostech neřeší, ani <xref:System.IAsyncResult> vzor:

- Blokování čekání na jeden<xref:System.IAsyncResult>

- Blokování čekání na mnoho <xref:System.IAsyncResult> objektů

- Cyklické dotazování na dokončení<xref:System.IAsyncResult>

Tyto scénáře můžete vyřešit pomocí vzoru založeného na událostech, ale je to obtížnější, než pomocí <xref:System.IAsyncResult> vzoru.

Vývojáři často používají <xref:System.IAsyncResult> vzory pro služby, které mají typicky vysoké požadavky na výkon. Například cyklické dotazování pro scénář dokončení je vysoce výkonná serverová technika.

Kromě toho je vzor založený na událostech méně efektivní než <xref:System.IAsyncResult> vzor, protože vytváří více objektů, zejména <xref:System.EventArgs> a, protože provádí synchronizaci mezi vlákny.

Následující seznam obsahuje doporučení, která se použijí, pokud se rozhodnete použít <xref:System.IAsyncResult> vzor:

- Vystavte <xref:System.IAsyncResult> vzor pouze v případě, že konkrétně požadujete podporu pro <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult> objekty nebo.

- Tento vzor zveřejňujte pouze v <xref:System.IAsyncResult> případě, že máte existující rozhraní API, které používá <xref:System.IAsyncResult> vzor.

- Pokud máte v závislosti na vzoru existující rozhraní API <xref:System.IAsyncResult> , zvažte také vystavení vzoru založeného na událostech v příští verzi.

- Vystavit <xref:System.IAsyncResult> vzor pouze v případě, že máte vysoce výkonné požadavky, které jste ověřili, nelze splnit vzor založený na událostech, ale lze jej splnit <xref:System.IAsyncResult> vzorem.

## <a name="see-also"></a>Viz také

- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](component-that-supports-the-event-based-asynchronous-pattern.md)
- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
- [Implementace asynchronního vzoru založeného na událostech](implementing-the-event-based-asynchronous-pattern.md)
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)
