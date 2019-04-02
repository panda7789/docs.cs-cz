---
ms.openlocfilehash: 97ca78e154eb25e863256e06caa119fe753bc344
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761289"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="1c94b-101">WPF kontroly pravopisu v textu povoleno ovládací prvky nebudou fungovat ve Windows 10 pro jazyky, které nejsou v seznamu jazyk operačního systému.</span><span class="sxs-lookup"><span data-stu-id="1c94b-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1c94b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1c94b-102">Details</span></span>|<span data-ttu-id="1c94b-103">Při spuštění ve Windows 10, nástroj pro kontrolu pravopisu nemusí fungovat pro ovládací prvky WPF textu povoleno, protože jsou k dispozici pouze pro jazyky, které jsou k dispozici v seznamu jazyků funkce platformy pro kontrolu pravopisu. Ve Windows 10 když jazyk se přidá do seznamu dostupných klávesnice, Windows automaticky stáhne a nainstaluje odpovídající funkce na vyžádání (zámořských) balíčku, které poskytuje funkce pro kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="1c94b-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="1c94b-104">Přidáním jazyk do seznamu jazyků bude podporovaný nástroj pro kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="1c94b-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="1c94b-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="1c94b-105">Suggestion</span></span>|<span data-ttu-id="1c94b-106">Mějte na paměti, že jazyk nebo text, který má být kontrola pravopisu je nutné přidat jako jazyk pro kontrolu pravopisu pro práci ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="1c94b-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="1c94b-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1c94b-107">Scope</span></span>|<span data-ttu-id="1c94b-108">Edge</span><span class="sxs-lookup"><span data-stu-id="1c94b-108">Edge</span></span>|
|<span data-ttu-id="1c94b-109">Version</span><span class="sxs-lookup"><span data-stu-id="1c94b-109">Version</span></span>|<span data-ttu-id="1c94b-110">4.6</span><span class="sxs-lookup"><span data-stu-id="1c94b-110">4.6</span></span>|
|<span data-ttu-id="1c94b-111">Type</span><span class="sxs-lookup"><span data-stu-id="1c94b-111">Type</span></span>|<span data-ttu-id="1c94b-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1c94b-112">Runtime</span></span>|

