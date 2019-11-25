---
title: 'Postupy: Generování sestavení vzájemné spolupráce z knihoven typů'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: f4f099dfaf5ff02edd3958d7eab9354ce727a239
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281806"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="71b4a-102">Postupy: Generování sestavení vzájemné spolupráce z knihoven typů</span><span class="sxs-lookup"><span data-stu-id="71b4a-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="71b4a-103">Modul pro [Import knihovny typů (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) je nástroj příkazového řádku, který převede třídy coclass a rozhraní, které jsou obsaženy v knihovně typů modelu COM, na metadata.</span><span class="sxs-lookup"><span data-stu-id="71b4a-103">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="71b4a-104">Tento nástroj vytvoří definiční sestavení a obor názvů pro informace o typu automaticky.</span><span class="sxs-lookup"><span data-stu-id="71b4a-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="71b4a-105">Po zpřístupnění metadat třídy mohou spravované klienty vytvářet instance typu modelu COM a volat jeho metody, stejně jako by šlo o instanci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="71b4a-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="71b4a-106">Nástroj Tlbimp. exe převede celou knihovnu typů na metadata najednou a nemůže generovat informace o typu pro podmnožinu typů definovaných v knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="71b4a-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="71b4a-107">Generování sestavení vzájemné spolupráce z knihovny typů</span><span class="sxs-lookup"><span data-stu-id="71b4a-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="71b4a-108">Použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="71b4a-108">Use the following command:</span></span>  
  
     <span data-ttu-id="71b4a-109">**tlbimp** \<*type-library-File*></span><span class="sxs-lookup"><span data-stu-id="71b4a-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="71b4a-110">Přidání přepínače **/out:** vytvoří definiční sestavení se změněným názvem, například LOANLib. dll.</span><span class="sxs-lookup"><span data-stu-id="71b4a-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="71b4a-111">Změna názvu definičního sestavení může zjednodušit jeho odlišení od původní knihovny DLL modelu COM a zabránit problémům, ke kterým může dojít, pokud mají duplicitní názvy.</span><span class="sxs-lookup"><span data-stu-id="71b4a-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71b4a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="71b4a-112">Example</span></span>  
 <span data-ttu-id="71b4a-113">Následující příkaz vytvoří sestavení LOANLib. dll v oboru názvů `Loanlib`.</span><span class="sxs-lookup"><span data-stu-id="71b4a-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="71b4a-114">Následující příkaz vytvoří definiční sestavení se změněným názvem (LOANLib. dll).</span><span class="sxs-lookup"><span data-stu-id="71b4a-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="71b4a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71b4a-115">See also</span></span>

- [<span data-ttu-id="71b4a-116">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="71b4a-116">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="71b4a-117">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="71b4a-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
