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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a3ee82a9091f0caeee010ec79632ce703efb589
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338836"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="f8349-102">Postupy: Generování sestavení vzájemné spolupráce z knihoven typů</span><span class="sxs-lookup"><span data-stu-id="f8349-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="f8349-103">[Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) je nástroj příkazového řádku, který převádí třídy typu coclass a rozhraní, které jsou obsaženy v knihovně typů modelu COM na metadata.</span><span class="sxs-lookup"><span data-stu-id="f8349-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="f8349-104">Tento nástroj automaticky vytvoří definiční sestavení a oboru názvů pro informace o typu.</span><span class="sxs-lookup"><span data-stu-id="f8349-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="f8349-105">Po metadata třídy jsou k dispozici, spravovaných klientů můžete vytvořit instance daného typu modelu COM a volat jeho metody, stejně jako by šlo instanci .NET.</span><span class="sxs-lookup"><span data-stu-id="f8349-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="f8349-106">Tlbimp.exe najednou převede celé knihovny typů na metadata a nemůže generovat informace o typu pro podmnožinu typů definovaných v knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="f8349-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="f8349-107">Ke generování sestavení vzájemné spolupráce z knihovny typů</span><span class="sxs-lookup"><span data-stu-id="f8349-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="f8349-108">Použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f8349-108">Use the following command:</span></span>  
  
     <span data-ttu-id="f8349-109">**Tlbimp** \< *soubor knihovny typů*></span><span class="sxs-lookup"><span data-stu-id="f8349-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="f8349-110">Přidávání **/out:** definiční sestavení s upravený název, jako je například LOANLib.dll vytváří přepínač.</span><span class="sxs-lookup"><span data-stu-id="f8349-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="f8349-111">Změna názvu sestavení vzájemné spolupráce pomáhá odlišil od původní knihovnu DLL modelu COM a zabránit problémům, které mohou nastat z s duplicitními názvy.</span><span class="sxs-lookup"><span data-stu-id="f8349-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8349-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8349-112">Example</span></span>  
 <span data-ttu-id="f8349-113">Následující příkaz vytvoří sestavení Loanlib.dll v `Loanlib` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f8349-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="f8349-114">Následující příkaz vygeneruje sestavení vzájemné spolupráce s upravený název (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="f8349-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8349-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8349-115">See also</span></span>

- [<span data-ttu-id="f8349-116">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="f8349-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="f8349-117">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f8349-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
