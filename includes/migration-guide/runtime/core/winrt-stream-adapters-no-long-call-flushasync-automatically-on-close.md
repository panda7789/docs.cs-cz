---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235307"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="b78bc-101">Adaptéry WinRT stream už se nejedná volání FlushAsync automaticky při zavření</span><span class="sxs-lookup"><span data-stu-id="b78bc-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b78bc-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b78bc-102">Details</span></span>|<span data-ttu-id="b78bc-103">Adaptéry datového proudu Windows Runtime v aplikacích pro Windows Store, už nebude volat metodu FlushAsync z metody Dispose.</span><span class="sxs-lookup"><span data-stu-id="b78bc-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="b78bc-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="b78bc-104">Suggestion</span></span>|<span data-ttu-id="b78bc-105">Tato změna by měl být průhledná.</span><span class="sxs-lookup"><span data-stu-id="b78bc-105">This change should be transparent.</span></span> <span data-ttu-id="b78bc-106">Vývojářům můžete obnovit předchozí chování napsáním kódu takto:</span><span class="sxs-lookup"><span data-stu-id="b78bc-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="b78bc-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b78bc-107">Scope</span></span>|<span data-ttu-id="b78bc-108">Transparentní</span><span class="sxs-lookup"><span data-stu-id="b78bc-108">Transparent</span></span>|
|<span data-ttu-id="b78bc-109">Version</span><span class="sxs-lookup"><span data-stu-id="b78bc-109">Version</span></span>|<span data-ttu-id="b78bc-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="b78bc-110">4.5.1</span></span>|
|<span data-ttu-id="b78bc-111">Type</span><span class="sxs-lookup"><span data-stu-id="b78bc-111">Type</span></span>|<span data-ttu-id="b78bc-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="b78bc-112">Runtime</span></span>|
