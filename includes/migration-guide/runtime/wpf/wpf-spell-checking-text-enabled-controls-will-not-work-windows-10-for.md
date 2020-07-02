---
ms.openlocfilehash: 1d2e4a058008676c6ea85becebd4bb9220569ef3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621160"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="4f9ad-101">Kontrola pravopisu v jazyce WPF v ovládacích prvcích s podporou textu nebude ve Windows 10 fungovat pro jazyky, které nejsou v seznamu vstupních jazyků v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="4f9ad-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="4f9ad-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4f9ad-102">Details</span></span>

<span data-ttu-id="4f9ad-103">Při spuštění ve Windows 10 nemusí kontrola pravopisu fungovat pro ovládací prvky s povoleným textem WPF, protože možnosti kontroly pravopisu platformy jsou dostupné jenom pro jazyky, které jsou k dispozici v seznamu vstupní jazyky. V systému Windows 10 se při přidání jazyka do seznamu dostupných klávesnic automaticky stáhne a nainstaluje odpovídající balíček funkce na vyžádání (FRANCOUZSKÝch), který poskytuje funkce kontroly pravopisu.</span><span class="sxs-lookup"><span data-stu-id="4f9ad-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="4f9ad-104">Když přidáte jazyk do seznamu vstupní jazyky, bude se tato kontrola pravopisu podporovat.</span><span class="sxs-lookup"><span data-stu-id="4f9ad-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4f9ad-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="4f9ad-105">Suggestion</span></span>

<span data-ttu-id="4f9ad-106">Počítejte s tím, že jazyk nebo text, který má být kontrolován pravopisem, musí být přidán jako vstupní jazyk pro kontrolu pravopisu pro práci ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="4f9ad-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="4f9ad-107">Name</span><span class="sxs-lookup"><span data-stu-id="4f9ad-107">Name</span></span>    | <span data-ttu-id="4f9ad-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4f9ad-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4f9ad-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4f9ad-109">Scope</span></span>   |<span data-ttu-id="4f9ad-110">Edge</span><span class="sxs-lookup"><span data-stu-id="4f9ad-110">Edge</span></span>|
|<span data-ttu-id="4f9ad-111">Verze</span><span class="sxs-lookup"><span data-stu-id="4f9ad-111">Version</span></span>|<span data-ttu-id="4f9ad-112">4.6</span><span class="sxs-lookup"><span data-stu-id="4f9ad-112">4.6</span></span>|
|<span data-ttu-id="4f9ad-113">Typ</span><span class="sxs-lookup"><span data-stu-id="4f9ad-113">Type</span></span>|<span data-ttu-id="4f9ad-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4f9ad-114">Runtime</span></span>|
