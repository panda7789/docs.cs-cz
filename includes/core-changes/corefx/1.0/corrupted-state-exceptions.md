---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135620"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a><span data-ttu-id="0b4c3-101">Zpracování výjimek poškozených stavů se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="0b4c3-101">Handling corrupted state exceptions is not supported</span></span>

<span data-ttu-id="0b4c3-102">Manipulace s poškozenými výjimkami stavu procesu v rozhraní .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="0b4c3-102">Handling corrupted-process-state exceptions in .NET Core is not supported.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0b4c3-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="0b4c3-103">Change description</span></span>

<span data-ttu-id="0b4c3-104">Dříve mohly být poškozené výjimky stavu procesu zachyceny a zpracovány obslužnými rutinami výjimek spravovaného kódu, například pomocí příkazu [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="0b4c3-104">Previously, corrupted-process-state exceptions could be caught and handled by managed code exception handlers, for example, by using a [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) statement in C#.</span></span>

<span data-ttu-id="0b4c3-105">Počínaje rozhraním .NET Core 1,0 nemohou výjimky stavu poškozeného procesu zpracovat spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="0b4c3-105">Starting in .NET Core 1.0, corrupted-process-state exceptions cannot be handled by managed code.</span></span> <span data-ttu-id="0b4c3-106">Modul CLR (Common Language Runtime) neposkytuje do spravovaného kódu výjimky nepoškozených stavových procesů.</span><span class="sxs-lookup"><span data-stu-id="0b4c3-106">The common language runtime doesn't deliver corrupted-process-state exceptions to managed code.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0b4c3-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="0b4c3-107">Version introduced</span></span>

<span data-ttu-id="0b4c3-108">1.0</span><span class="sxs-lookup"><span data-stu-id="0b4c3-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0b4c3-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0b4c3-109">Recommended action</span></span>

<span data-ttu-id="0b4c3-110">Vyhněte se nutnosti zpracovat výjimky poškozeného procesu tím, že se postarou o situace, které k nim mají zájem.</span><span class="sxs-lookup"><span data-stu-id="0b4c3-110">Avoid the need to handle corrupted-process-state exceptions by addressing the situations that lead to them instead.</span></span> <span data-ttu-id="0b4c3-111">Pokud je nezbytně nutné pro zpracování výjimek stavu poškozeného procesu, napište obslužnou rutinu výjimky v kódu C nebo C++.</span><span class="sxs-lookup"><span data-stu-id="0b4c3-111">If it's absolutely necessary to handle corrupted-process-state exceptions, write the exception handler in C or C++ code.</span></span>

#### <a name="category"></a><span data-ttu-id="0b4c3-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0b4c3-112">Category</span></span>

<span data-ttu-id="0b4c3-113">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="0b4c3-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0b4c3-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0b4c3-114">Affected APIs</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [<span data-ttu-id="0b4c3-115">element legacyCorruptedStateExceptionsPolicy</span><span class="sxs-lookup"><span data-stu-id="0b4c3-115">legacyCorruptedStateExceptionsPolicy element</span></span>](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
