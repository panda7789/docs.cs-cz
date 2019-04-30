---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649037"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="99803-101">Adaptéry WinRT stream už se nejedná volání FlushAsync automaticky při zavření</span><span class="sxs-lookup"><span data-stu-id="99803-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="99803-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="99803-102">Details</span></span>|<span data-ttu-id="99803-103">Adaptéry datového proudu Windows Runtime v aplikacích pro Windows Store, už nebude volat metodu FlushAsync z metody Dispose.</span><span class="sxs-lookup"><span data-stu-id="99803-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="99803-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="99803-104">Suggestion</span></span>|<span data-ttu-id="99803-105">Tato změna by měl být průhledná.</span><span class="sxs-lookup"><span data-stu-id="99803-105">This change should be transparent.</span></span> <span data-ttu-id="99803-106">Vývojářům můžete obnovit předchozí chování napsáním kódu takto:</span><span class="sxs-lookup"><span data-stu-id="99803-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="99803-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="99803-107">Scope</span></span>|<span data-ttu-id="99803-108">Transparentní</span><span class="sxs-lookup"><span data-stu-id="99803-108">Transparent</span></span>|
|<span data-ttu-id="99803-109">Version</span><span class="sxs-lookup"><span data-stu-id="99803-109">Version</span></span>|<span data-ttu-id="99803-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="99803-110">4.5.1</span></span>|
|<span data-ttu-id="99803-111">Type</span><span class="sxs-lookup"><span data-stu-id="99803-111">Type</span></span>|<span data-ttu-id="99803-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="99803-112">Runtime</span></span>|
