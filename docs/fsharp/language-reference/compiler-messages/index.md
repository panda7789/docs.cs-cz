---
title: Chyby a upozornění kompilátoru
description: Popisy a řešení pro chyby a upozornění, která F# kompilátor vygeneruje
ms.date: 12/21/2019
ms.openlocfilehash: 52d94475e8b0195281d6244230c50c8f64230aeb
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76929557"
---
# <a name="f-compiler-messages"></a><span data-ttu-id="19fe8-103">F#zprávy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="19fe8-103">F# compiler messages</span></span>

<span data-ttu-id="19fe8-104">Tato část podrobně popisuje chyby kompilátoru a upozornění, F# které kompilátor vygeneruje pro určité konstrukce.</span><span class="sxs-lookup"><span data-stu-id="19fe8-104">This section details compiler errors and warnings that the F# compiler will emit for certain constructs.</span></span> <span data-ttu-id="19fe8-105">Výchozí sady chyb lze změnit pomocí:</span><span class="sxs-lookup"><span data-stu-id="19fe8-105">The default sets of errors can be changed by:</span></span>

- <span data-ttu-id="19fe8-106">Zpracování specifických upozornění, jako kdyby došlo k chybám pomocí možnosti kompilátoru `-warnaserror+`,</span><span class="sxs-lookup"><span data-stu-id="19fe8-106">Treating specific warnings as if they were errors by using the `-warnaserror+` compiler option,</span></span>

- <span data-ttu-id="19fe8-107">Ignorování konkrétních upozornění pomocí možnosti kompilátoru `-nowarn`</span><span class="sxs-lookup"><span data-stu-id="19fe8-107">Ignoring specific warnings by using the `-nowarn` compiler option</span></span>

<span data-ttu-id="19fe8-108">Pokud v této části ještě není zaznamenáno určité upozornění nebo chyba, přejdete na konec této stránky a odešlete zpětnou vazbu, která obsahuje číslo nebo text chyby.</span><span class="sxs-lookup"><span data-stu-id="19fe8-108">If a particular warning or error is not yet recorded in this section, go to the end of this page and send feedback that includes the number or text of the error.</span></span>

## <a name="see-also"></a><span data-ttu-id="19fe8-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19fe8-109">See also</span></span>

- [<span data-ttu-id="19fe8-110">F#Možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="19fe8-110">F# Compiler Options</span></span>](../compiler-options.md)
