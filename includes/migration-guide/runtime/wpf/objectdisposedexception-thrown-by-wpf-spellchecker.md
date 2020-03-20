---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802535"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="3d9a6-101">ObjectDisposedException vyvolána WPF kontrola pravopisu</span><span class="sxs-lookup"><span data-stu-id="3d9a6-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3d9a6-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3d9a6-102">Details</span></span>|<span data-ttu-id="3d9a6-103">WPF aplikace občas selhání během <xref:System.ObjectDisposedException?displayProperty=name> vypnutí aplikace s vyvolána kontrola pravopisu.</span><span class="sxs-lookup"><span data-stu-id="3d9a6-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="3d9a6-104">To je opraveno v rozhraní .NET Framework 4.7 WPF zpracováním výjimky řádně a tím zajistit, že aplikace již nejsou nepříznivě ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="3d9a6-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="3d9a6-105">Je třeba poznamenat, že příležitostné výjimky první šance by i nadále být pozorovány v aplikacích spuštěných v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="3d9a6-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="3d9a6-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="3d9a6-106">Suggestion</span></span>|<span data-ttu-id="3d9a6-107">Upgrade na rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="3d9a6-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="3d9a6-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3d9a6-108">Scope</span></span>|<span data-ttu-id="3d9a6-109">Edge</span><span class="sxs-lookup"><span data-stu-id="3d9a6-109">Edge</span></span>|
|<span data-ttu-id="3d9a6-110">Version</span><span class="sxs-lookup"><span data-stu-id="3d9a6-110">Version</span></span>|<span data-ttu-id="3d9a6-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="3d9a6-111">4.6.1</span></span>|
|<span data-ttu-id="3d9a6-112">Typ</span><span class="sxs-lookup"><span data-stu-id="3d9a6-112">Type</span></span>|<span data-ttu-id="3d9a6-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3d9a6-113">Runtime</span></span>|
