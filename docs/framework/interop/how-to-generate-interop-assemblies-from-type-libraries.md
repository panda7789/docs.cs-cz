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
ms.openlocfilehash: aea23daff28b50678b9fa7902857fc302494c4a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387728"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="fe4ce-102">Postupy: Generování sestavení vzájemné spolupráce z knihoven typů</span><span class="sxs-lookup"><span data-stu-id="fe4ce-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="fe4ce-103">[Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) je nástroj příkazového řádku, který převádí třídy typu coclass a rozhraní, které jsou součástí modelu COM knihovny typů pro metadata.</span><span class="sxs-lookup"><span data-stu-id="fe4ce-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="fe4ce-104">Tento nástroj automaticky vytvoří sestavení vzájemné spolupráce a obor názvů pro informace o typu.</span><span class="sxs-lookup"><span data-stu-id="fe4ce-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="fe4ce-105">Po metadata třídy je k dispozici, spravovaných klientů můžete vytvořit instance typu COM a volat její metody stejně, jako by šlo instance rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="fe4ce-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="fe4ce-106">Tlbimp.exe převede celý typ knihovny na metadata najednou a nelze generovat informace o typu pro podmnožinu typy definované v knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fe4ce-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="fe4ce-107">Ke generování sestavení vzájemné spolupráce z knihovny typů</span><span class="sxs-lookup"><span data-stu-id="fe4ce-107">To generate an interop assembly from a type library</span></span>  
  
1.  <span data-ttu-id="fe4ce-108">Použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fe4ce-108">Use the following command:</span></span>  
  
     <span data-ttu-id="fe4ce-109">**Tlbimp** \< *soubor knihovny typů*></span><span class="sxs-lookup"><span data-stu-id="fe4ce-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="fe4ce-110">Přidávání **/out:** přepínač vytváří sestavení spolupráce s změnit název, jako je například LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="fe4ce-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="fe4ce-111">Změna názvu sestavení vzájemné spolupráce může pomoci ho odlišuje od původního DLL COM a zabránit problémům, které se můžou vyskytnout s duplicitními názvy.</span><span class="sxs-lookup"><span data-stu-id="fe4ce-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe4ce-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe4ce-112">Example</span></span>  
 <span data-ttu-id="fe4ce-113">Následující příkaz vytvoří Loanlib.dll sestavení v `Loanlib` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fe4ce-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.dll  
```  
  
 <span data-ttu-id="fe4ce-114">Následující příkaz vytvoří spolupráce sestavení s názvem změněna (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="fe4ce-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe4ce-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe4ce-115">See Also</span></span>  
 [<span data-ttu-id="fe4ce-116">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="fe4ce-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="fe4ce-117">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fe4ce-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
