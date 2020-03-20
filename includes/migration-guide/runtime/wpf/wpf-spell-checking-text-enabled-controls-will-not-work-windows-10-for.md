---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858434"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="4d61d-101">WPF kontrola pravopisu v text-dát povolené ovládací prvky nebude fungovat v systému Windows 10 pro jazyky, které nejsou v seznamu jazyka zadávání operačního systému</span><span class="sxs-lookup"><span data-stu-id="4d61d-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4d61d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4d61d-102">Details</span></span>|<span data-ttu-id="4d61d-103">Při spuštění v systému Windows 10 nemusí kontrola pravopisu fungovat pro ovládací prvky s podporou textu WPF, protože funkce kontroly pravopisu platformy jsou k dispozici pouze pro jazyky v seznamu vstupních jazyků. Při přidání jazyka do seznamu dostupných klávesnic systém Windows při přidání jazyka do seznamu dostupných klávesnic automaticky stáhne a nainstaluje odpovídající balíček Funkce na vyžádání (FOD), který poskytuje funkce kontroly pravopisu.</span><span class="sxs-lookup"><span data-stu-id="4d61d-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="4d61d-104">Přidáním jazyka do seznamu vstupních jazyků bude kontrola pravopisu podporována.</span><span class="sxs-lookup"><span data-stu-id="4d61d-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="4d61d-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="4d61d-105">Suggestion</span></span>|<span data-ttu-id="4d61d-106">Uvědomte si, že jazyk nebo text, který má být kontrolován pravopisem, musí být přidán jako vstupní jazyk pro kontrolu pravopisu, aby fungoval v systému Windows 10.</span><span class="sxs-lookup"><span data-stu-id="4d61d-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="4d61d-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4d61d-107">Scope</span></span>|<span data-ttu-id="4d61d-108">Edge</span><span class="sxs-lookup"><span data-stu-id="4d61d-108">Edge</span></span>|
|<span data-ttu-id="4d61d-109">Version</span><span class="sxs-lookup"><span data-stu-id="4d61d-109">Version</span></span>|<span data-ttu-id="4d61d-110">4.6</span><span class="sxs-lookup"><span data-stu-id="4d61d-110">4.6</span></span>|
|<span data-ttu-id="4d61d-111">Typ</span><span class="sxs-lookup"><span data-stu-id="4d61d-111">Type</span></span>|<span data-ttu-id="4d61d-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4d61d-112">Runtime</span></span>|
