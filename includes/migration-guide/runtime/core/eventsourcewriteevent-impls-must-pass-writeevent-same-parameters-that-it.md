---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619975"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="09100-101">EventSource. WriteEvent impls musí předat WriteEvent stejné parametry (plus ID).</span><span class="sxs-lookup"><span data-stu-id="09100-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

#### <a name="details"></a><span data-ttu-id="09100-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="09100-102">Details</span></span>

<span data-ttu-id="09100-103">Modul runtime nyní vynutil kontrakt, který určuje následující: třída odvozená z <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> , která definuje metodu události ETW, musí volat metodu základní třídy <code>EventSource.WriteEvent</code> s ID události následovaný stejnými argumenty, které byla metoda události ETW úspěšná.</span><span class="sxs-lookup"><span data-stu-id="09100-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="09100-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="09100-104">Suggestion</span></span>

<span data-ttu-id="09100-105"><xref:System.IndexOutOfRangeException?displayProperty=fullName>Výjimka je vyvolána, pokud je <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> v procesu načtena data pro zdroj události, který je v rozporu s touto smlouvou.</span><span class="sxs-lookup"><span data-stu-id="09100-105">An <xref:System.IndexOutOfRangeException?displayProperty=fullName> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process for an event source that violates this contract.</span></span>

| <span data-ttu-id="09100-106">Name</span><span class="sxs-lookup"><span data-stu-id="09100-106">Name</span></span>    | <span data-ttu-id="09100-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="09100-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="09100-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="09100-108">Scope</span></span>   |<span data-ttu-id="09100-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="09100-109">Minor</span></span>|
|<span data-ttu-id="09100-110">Verze</span><span class="sxs-lookup"><span data-stu-id="09100-110">Version</span></span>|<span data-ttu-id="09100-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="09100-111">4.5.1</span></span>|
|<span data-ttu-id="09100-112">Typ</span><span class="sxs-lookup"><span data-stu-id="09100-112">Type</span></span>|<span data-ttu-id="09100-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="09100-113">Runtime</span></span>|
