---
ms.openlocfilehash: 27bd38edd81abb5ce5893021bcc96e7eeae7ae2c
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140897"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="7d006-101">Odebrané ovládací prvky stavového řádku</span><span class="sxs-lookup"><span data-stu-id="7d006-101">Removed status bar controls</span></span>

<span data-ttu-id="7d006-102">Od verze .NET 5,0 Preview 1 nejsou již některé ovládací prvky model Windows Forms k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7d006-102">Starting in .NET 5.0 Preview 1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7d006-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="7d006-103">Change description</span></span>

<span data-ttu-id="7d006-104">Od verze .NET 5,0 Preview 1 nejsou již některé ovládací prvky model Windows Forms související se stavovým řádkem k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7d006-104">Starting with .NET 5.0 Preview 1, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="7d006-105">Náhradní ovládací prvky, které mají lepší návrh a podporu, byly zavedeny v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="7d006-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="7d006-106">Zastaralé ovládací prvky byly předtím odebrány z nástrojů návrháře, ale byly stále k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="7d006-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="7d006-107">Nyní byly zcela odebrány.</span><span class="sxs-lookup"><span data-stu-id="7d006-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="7d006-108">Následující typy již nejsou k dispozici:</span><span class="sxs-lookup"><span data-stu-id="7d006-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="7d006-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="7d006-109">Version introduced</span></span>

<span data-ttu-id="7d006-110">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="7d006-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7d006-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7d006-111">Recommended action</span></span>

<span data-ttu-id="7d006-112">Přejděte na náhradní rozhraní API pro tyto ovládací prvky a jejich scénáře:</span><span class="sxs-lookup"><span data-stu-id="7d006-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="7d006-113">Starý ovládací prvek (API)</span><span class="sxs-lookup"><span data-stu-id="7d006-113">Old Control (API)</span></span> | <span data-ttu-id="7d006-114">Doporučená náhrada</span><span class="sxs-lookup"><span data-stu-id="7d006-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="7d006-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="7d006-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="7d006-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="7d006-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="7d006-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7d006-117">Category</span></span>

<span data-ttu-id="7d006-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d006-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7d006-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7d006-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!-- 

### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
