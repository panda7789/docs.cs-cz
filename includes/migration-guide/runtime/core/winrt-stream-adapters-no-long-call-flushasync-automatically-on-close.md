---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619996"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="8214e-101">Adaptéry WinRT streamu bez dlouhého volání FlushAsync automaticky při zavření</span><span class="sxs-lookup"><span data-stu-id="8214e-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="8214e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8214e-102">Details</span></span>

<span data-ttu-id="8214e-103">V aplikacích pro Windows Store prostředí Windows Runtime adaptéry streamování již nevolají metodu FlushAsync z metody Dispose.</span><span class="sxs-lookup"><span data-stu-id="8214e-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8214e-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="8214e-104">Suggestion</span></span>

<span data-ttu-id="8214e-105">Tato změna by měla být transparentní.</span><span class="sxs-lookup"><span data-stu-id="8214e-105">This change should be transparent.</span></span> <span data-ttu-id="8214e-106">Vývojáři mohou obnovit předchozí chování tak, že napíše kód takto:</span><span class="sxs-lookup"><span data-stu-id="8214e-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="8214e-107">Name</span><span class="sxs-lookup"><span data-stu-id="8214e-107">Name</span></span>    | <span data-ttu-id="8214e-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8214e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8214e-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8214e-109">Scope</span></span>   |<span data-ttu-id="8214e-110">Průhlednost</span><span class="sxs-lookup"><span data-stu-id="8214e-110">Transparent</span></span>|
|<span data-ttu-id="8214e-111">Verze</span><span class="sxs-lookup"><span data-stu-id="8214e-111">Version</span></span>|<span data-ttu-id="8214e-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8214e-112">4.5.1</span></span>|
|<span data-ttu-id="8214e-113">Typ</span><span class="sxs-lookup"><span data-stu-id="8214e-113">Type</span></span>|<span data-ttu-id="8214e-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="8214e-114">Runtime</span></span>|
