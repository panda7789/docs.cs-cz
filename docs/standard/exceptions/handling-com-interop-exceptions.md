---
title: Zpracování výjimek vzájemné spolupráce COM
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 17cd739ac40b43bdd4a93b83a4ab9d0d92400e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708929"
---
# <a name="handling-com-interop-exceptions"></a>Zpracování výjimek vzájemné spolupráce COM
Spravovaný a nespravovaný kód může spolupracovat na zpracování výjimek. Pokud metoda vyvolá výjimku ve spravovaném kódu, může soubor Runtime společného jazyka předat objektu COM. Pokud metoda selže v nespravovaném kódu vrácením selhání HRESULT, runtime vyvolá výjimku, která může být zachycena spravovaným kódem.  
  
 Runtime automaticky mapuje HRESULT z komop na konkrétnější výjimky. Například E_ACCESSDENIED <xref:System.UnauthorizedAccessException>se stane <xref:System.OutOfMemoryException>, E_OUTOFMEMORY se stane a tak dále.  
  
 Pokud HRESULT je vlastní výsledek nebo pokud není znám a runtime, <xref:System.Runtime.InteropServices.COMException> runtime předá obecné klientovi. Vlastnost **ErrorCode** **výjimky COMException** obsahuje hodnotu HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Práce s IErrorInfo  
 Při předání chyby z com spravovaného kódu, runtime naplní objekt výjimky s informacemi o chybě. Objekty COM, které podporují IErrorInfo a vrátí funkce HRESULTS, poskytují tyto informace výjimkám spravovaného kódu. Například runtime mapuje popis z chyby COM <xref:System.Exception.Message%2A> na vlastnost výjimky. Pokud HRESULT poskytuje žádné další informace o chybě, runtime vyplní mnoho vlastností výjimky s výchozí hodnoty.  
  
 Pokud metoda selže v nespravovaném kódu, může být výjimka předána segmentu spravovaného kódu. Téma [HRESULTS a Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) obsahuje tabulku zobrazující, jak HRESULTS mapuje na objekty výjimek za běhu.  

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
