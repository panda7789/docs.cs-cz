---
ms.openlocfilehash: 29c66edfeb1690199aac39b9c3076d161b2075d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621151"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="47d49-101">Kontrakt. invariantní nebo kontrakt. vyžaduje, \<TException> aby nebral řetězec. IsNullOrEmpty na hodnotu Pure.</span><span class="sxs-lookup"><span data-stu-id="47d49-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="47d49-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="47d49-102">Details</span></span>

<span data-ttu-id="47d49-103">Pro aplikace, které cílí na .NET Framework 4.6.1, pokud invariantní smlouva pro <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> nebo smlouvu předběžných podmínek pro <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> volání <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody, Rewrite vygeneruje upozornění kompilátoru CC1036: &quot; zjištěno volání metody System. String. IsNullOrWhteSpace (System. String) bez [Pure] v metodě. &quot; Toto je upozornění kompilátoru, nikoli Chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="47d49-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="47d49-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="47d49-104">Suggestion</span></span>

<span data-ttu-id="47d49-105">Toto chování bylo vyřešeno [#339 problému na GitHubu](https://github.com/Microsoft/CodeContracts/issues/339).</span><span class="sxs-lookup"><span data-stu-id="47d49-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="47d49-106">Chcete-li odstranit toto upozornění, můžete stáhnout a zkompilovat aktualizovanou verzi zdrojového kódu pro nástroj Code Contracts z [GitHubu](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="47d49-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="47d49-107">Informace o stažení najdete v dolní části stránky.</span><span class="sxs-lookup"><span data-stu-id="47d49-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="47d49-108">Name</span><span class="sxs-lookup"><span data-stu-id="47d49-108">Name</span></span>    | <span data-ttu-id="47d49-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="47d49-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="47d49-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="47d49-110">Scope</span></span>   |<span data-ttu-id="47d49-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="47d49-111">Minor</span></span>|
|<span data-ttu-id="47d49-112">Verze</span><span class="sxs-lookup"><span data-stu-id="47d49-112">Version</span></span>|<span data-ttu-id="47d49-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="47d49-113">4.6.1</span></span>|
|<span data-ttu-id="47d49-114">Typ</span><span class="sxs-lookup"><span data-stu-id="47d49-114">Type</span></span>|<span data-ttu-id="47d49-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="47d49-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="47d49-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="47d49-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
