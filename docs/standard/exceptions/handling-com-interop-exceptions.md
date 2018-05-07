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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f4429d50f6b7646cb75fad44957a98812282928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="handling-com-interop-exceptions"></a>Zpracování výjimek vzájemné spolupráce COM
Spravovat a nespravovaného kódu můžou spolupracovat a zpracování výjimek. Pokud metoda vyvolá výjimku ve spravovaném kódu, můžete modul common language runtime předat HRESULT objektu COM. Pokud metoda selže v nespravovaném kódu vrácením selhání HRESULT, modul runtime vyvolá výjimku, která může být zachycen spravovaného kódu.  
  
 Modul runtime automaticky mapuje HRESULT z zprostředkovatel komunikace s objekty COM pro více specifické výjimky. Například E_ACCESSDENIED bude <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY se stane <xref:System.OutOfMemoryException>a tak dále.  
  
 Pokud je hodnota HRESULT vlastní výsledek nebo pokud Neznámý modulu runtime, modul runtime předá obecný <xref:System.Runtime.InteropServices.COMException> klientovi. **ErrorCode** vlastnost **COMException** obsahuje hodnotu HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Práce s IErrorInfo  
 Když chybu předána do spravovaného kódu z modelu COM, modul runtime naplní objekt výjimky s informace o chybě. Objekty COM, které podporují IErrorInfo a vrátit hodnoty HRESULT předejte tyto informace k výjimkám spravovaného kódu. Například modul runtime mapuje popis z chyby COM s výjimkou <xref:System.Exception.Message%2A> vlastnost. Pokud HRESULT neposkytuje žádné další informace o chybě, modul runtime vyplní mnoho vlastností výjimky s výchozími hodnotami.  
  
 Pokud metoda selže v nespravovaném kódu, můžete předat výjimku segment spravovaného kódu. Téma [výsledků HRESULT a výjimek](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) obsahuje tabulku, která ukazuje, jak hodnoty HRESULT mapovat na objekty výjimek modulu runtime.  

## <a name="see-also"></a>Viz také
[Výjimky](index.md) 
