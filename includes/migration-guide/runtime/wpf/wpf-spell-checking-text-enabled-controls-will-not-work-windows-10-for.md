---
ms.openlocfilehash: 97ca78e154eb25e863256e06caa119fe753bc344
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858434"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="63bcd-101">WPF kontroly pravopisu v textu povoleno ovládací prvky nebudou fungovat ve Windows 10 pro jazyky, které nejsou v seznamu jazyk operačního systému.</span><span class="sxs-lookup"><span data-stu-id="63bcd-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="63bcd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="63bcd-102">Details</span></span>|<span data-ttu-id="63bcd-103">Při spuštění ve Windows 10, nástroj pro kontrolu pravopisu nemusí fungovat pro ovládací prvky WPF textu povoleno, protože jsou k dispozici pouze pro jazyky, které jsou k dispozici v seznamu jazyků funkce platformy pro kontrolu pravopisu. Ve Windows 10 když jazyk se přidá do seznamu dostupných klávesnice, Windows automaticky stáhne a nainstaluje odpovídající funkce na vyžádání (zámořských) balíčku, které poskytuje funkce pro kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="63bcd-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="63bcd-104">Přidáním jazyk do seznamu jazyků bude podporovaný nástroj pro kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="63bcd-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="63bcd-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="63bcd-105">Suggestion</span></span>|<span data-ttu-id="63bcd-106">Mějte na paměti, že jazyk nebo text, který má být kontrola pravopisu je nutné přidat jako jazyk pro kontrolu pravopisu pro práci ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="63bcd-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="63bcd-107">Scope</span><span class="sxs-lookup"><span data-stu-id="63bcd-107">Scope</span></span>|<span data-ttu-id="63bcd-108">Edge</span><span class="sxs-lookup"><span data-stu-id="63bcd-108">Edge</span></span>|
|<span data-ttu-id="63bcd-109">Version</span><span class="sxs-lookup"><span data-stu-id="63bcd-109">Version</span></span>|<span data-ttu-id="63bcd-110">4.6</span><span class="sxs-lookup"><span data-stu-id="63bcd-110">4.6</span></span>|
|<span data-ttu-id="63bcd-111">type</span><span class="sxs-lookup"><span data-stu-id="63bcd-111">Type</span></span>|<span data-ttu-id="63bcd-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="63bcd-112">Runtime</span></span>|

