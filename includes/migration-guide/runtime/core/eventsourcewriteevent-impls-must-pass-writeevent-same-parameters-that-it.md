---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803703"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="1d897-101">EventSource.WriteEvent impls musíte předat metodě WriteEvent stejné parametry, které obdržel (plus ID)</span><span class="sxs-lookup"><span data-stu-id="1d897-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1d897-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1d897-102">Details</span></span>|<span data-ttu-id="1d897-103">Runtime modul vynucuje nyní kontrakt, který určuje následující: Třída odvozená z <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> , který definuje ETW metodě události musí volat základní třídy <code>EventSource.WriteEvent</code> metoda s ID události, za nímž následuje stejné argumenty, které byla předána metodě události trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="1d897-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>|
|<span data-ttu-id="1d897-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="1d897-104">Suggestion</span></span>|<span data-ttu-id="1d897-105"><xref:System.IndexOutOfRangeException?displayProperty=name> Je vyvolána výjimka, pokud <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> přečte <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data v procesu pro zdroje událostí, která porušuje tento kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1d897-105">An <xref:System.IndexOutOfRangeException?displayProperty=name> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data in process for an event source that violates this contract.</span></span>|
|<span data-ttu-id="1d897-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1d897-106">Scope</span></span>|<span data-ttu-id="1d897-107">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="1d897-107">Minor</span></span>|
|<span data-ttu-id="1d897-108">Version</span><span class="sxs-lookup"><span data-stu-id="1d897-108">Version</span></span>|<span data-ttu-id="1d897-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="1d897-109">4.5.1</span></span>|
|<span data-ttu-id="1d897-110">Type</span><span class="sxs-lookup"><span data-stu-id="1d897-110">Type</span></span>|<span data-ttu-id="1d897-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1d897-111">Runtime</span></span>|
