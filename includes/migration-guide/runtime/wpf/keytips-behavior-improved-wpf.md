---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621115"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="2ee46-101">Vylepšení chování tipů v WPF</span><span class="sxs-lookup"><span data-stu-id="2ee46-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="2ee46-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2ee46-102">Details</span></span>

<span data-ttu-id="2ee46-103">Chování tipů kláves bylo upraveno tak, aby se v aplikacích Microsoft Word a Windows Explorer nastavila parita s chováním.</span><span class="sxs-lookup"><span data-stu-id="2ee46-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="2ee46-104">Tím, že zkontrolujete, jestli je stav KeyTip povolený nebo ne v případě, že se <xref:System.Windows.Input.KeyEventArgs.SystemKey> stiskne (konkrétně <xref:System.Windows.Input.Key> nebo <xref:System.Windows.Input.Key.F11> ) stisknutí, WPF zpracuje KeyTip klíče správně.</span><span class="sxs-lookup"><span data-stu-id="2ee46-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="2ee46-105">Pomocí klávesových tipů nyní můžete zavřít nabídku i v případě, že ji otevřete myší.</span><span class="sxs-lookup"><span data-stu-id="2ee46-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2ee46-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="2ee46-106">Suggestion</span></span>

<span data-ttu-id="2ee46-107">–</span><span class="sxs-lookup"><span data-stu-id="2ee46-107">N/A</span></span>

| <span data-ttu-id="2ee46-108">Name</span><span class="sxs-lookup"><span data-stu-id="2ee46-108">Name</span></span>    | <span data-ttu-id="2ee46-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2ee46-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2ee46-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2ee46-110">Scope</span></span>   |<span data-ttu-id="2ee46-111">Edge</span><span class="sxs-lookup"><span data-stu-id="2ee46-111">Edge</span></span>|
|<span data-ttu-id="2ee46-112">Verze</span><span class="sxs-lookup"><span data-stu-id="2ee46-112">Version</span></span>|<span data-ttu-id="2ee46-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="2ee46-113">4.7.2</span></span>|
|<span data-ttu-id="2ee46-114">Typ</span><span class="sxs-lookup"><span data-stu-id="2ee46-114">Type</span></span>|<span data-ttu-id="2ee46-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2ee46-115">Runtime</span></span>|
