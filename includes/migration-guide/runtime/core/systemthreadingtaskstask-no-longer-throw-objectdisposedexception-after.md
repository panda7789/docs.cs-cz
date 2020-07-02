---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619993"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="515a3-101">System. Threading. Tasks. Task již nevyvolává ObjectDisposedException po uvolnění objektu.</span><span class="sxs-lookup"><span data-stu-id="515a3-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="515a3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="515a3-102">Details</span></span>

<span data-ttu-id="515a3-103">S výjimkou <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> , <xref:System.Threading.Tasks.Task?displayProperty=fullName> metody již nevyvolávají <xref:System.ObjectDisposedException?displayProperty=fullName> výjimku po vyřazení objektu. Tato změna podporuje používání úkolů v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="515a3-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="515a3-104">Například metoda může vrátit úlohu uloženou v mezipaměti pro zastupování již dokončené operace namísto přidělení nové úlohy.</span><span class="sxs-lookup"><span data-stu-id="515a3-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="515a3-105">To nebylo v předchozích verzích rozhraní .NET Framework možné, protože příjemci úlohy s ní mohli nakládat.</span><span class="sxs-lookup"><span data-stu-id="515a3-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="515a3-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="515a3-106">Suggestion</span></span>

<span data-ttu-id="515a3-107">Uvědomte si, že metody úloh již nemusí být <xref:System.ObjectDisposedException?displayProperty=fullName> v případě uvolnění objektu vyhozeny.</span><span class="sxs-lookup"><span data-stu-id="515a3-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="515a3-108">Pokud byla aplikace v závislosti na této výjimce známa s tím, že byla úloha vyřazena, měla by být aktualizována tak, aby explicitně kontrolovala stav úlohy pomocí <xref:System.Threading.Tasks.Task.Status> .</span><span class="sxs-lookup"><span data-stu-id="515a3-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="515a3-109">Name</span><span class="sxs-lookup"><span data-stu-id="515a3-109">Name</span></span>    | <span data-ttu-id="515a3-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="515a3-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="515a3-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="515a3-111">Scope</span></span>   |<span data-ttu-id="515a3-112">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="515a3-112">Minor</span></span>|
|<span data-ttu-id="515a3-113">Verze</span><span class="sxs-lookup"><span data-stu-id="515a3-113">Version</span></span>|<span data-ttu-id="515a3-114">4.5</span><span class="sxs-lookup"><span data-stu-id="515a3-114">4.5</span></span>|
|<span data-ttu-id="515a3-115">Typ</span><span class="sxs-lookup"><span data-stu-id="515a3-115">Type</span></span>|<span data-ttu-id="515a3-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="515a3-116">Runtime</span></span>|
