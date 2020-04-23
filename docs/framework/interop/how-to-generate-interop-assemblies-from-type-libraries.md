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
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Postupy: Generování sestavení vzájemné spolupráce z knihoven typů
Modul pro [Import knihovny typů (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) je nástroj příkazového řádku, který převede třídy coclass a rozhraní, které jsou obsaženy v knihovně typů modelu COM, na metadata. Tento nástroj vytvoří definiční sestavení a obor názvů pro informace o typu automaticky. Po zpřístupnění metadat třídy mohou spravované klienty vytvářet instance typu modelu COM a volat jeho metody, stejně jako by šlo o instanci rozhraní .NET. Nástroj Tlbimp. exe převede celou knihovnu typů na metadata najednou a nemůže generovat informace o typu pro podmnožinu typů definovaných v knihovně typů.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Generování sestavení vzájemné spolupráce z knihovny typů  
  
1. Použijte následující příkaz:  
  
     **Tlbimp** \< *– typ knihovny – soubor*>  
  
     Přidání přepínače **/out:** vytvoří definiční sestavení se změněným názvem, například LOANLib. dll. Změna názvu definičního sestavení může zjednodušit jeho odlišení od původní knihovny DLL modelu COM a zabránit problémům, ke kterým může dojít, pokud mají duplicitní názvy.  
  
## <a name="example"></a>Příklad  
 Následující příkaz vytvoří sestavení LOANLib. dll v `Loanlib` oboru názvů.  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 Následující příkaz vytvoří definiční sestavení se změněným názvem (LOANLib. dll).  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Viz také

- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
