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
ms.openlocfilehash: 0a17752257589ea4ee4d9e58182d4448f02f6460
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970934"
---
# <a name="handling-com-interop-exceptions"></a>Zpracování výjimek vzájemné spolupráce COM
Spravovaného a nespravovaného kódu můžou spolupracovat a zpracování výjimek. Pokud metoda vyvolá výjimku ve spravovaném kódu, modul common language runtime lze předat HRESULT objektu COM. Jestliže metoda selže v nespravovaném kódu tak, že vrací selhání hodnoty HRESULT, modul runtime vyvolá výjimku, která může být zachycena spravovaným kódem.  
  
 Modul runtime automaticky mapuje HRESULT z komunikace s objekty COM pro více specifické výjimky. Například E_ACCESSDENIED stane <xref:System.UnauthorizedAccessException>, stane E_OUTOFMEMORY <xref:System.OutOfMemoryException>, a tak dále.  
  
 Pokud je vlastní výsledek HRESULT nebo pokud neznámý modul runtime, modul runtime předá obecný <xref:System.Runtime.InteropServices.COMException> do klienta. **ErrorCode** vlastnost **COMException** obsahuje hodnotu HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Práce s IErrorInfo  
 Při chybě je předán z modelu COM pro spravovaný kód, modul runtime naplní objekt výjimky s informacemi o chybě. Objekty COM, které podporují IErrorInfo a vrátí výsledky HRESULT poskytnout tyto informace do spravovaného kódu výjimky. Například modul runtime mapuje popisu v chybové zprávě modelu COM s výjimkou <xref:System.Exception.Message%2A> vlastnost. Pokud HRESULT neposkytuje žádné další informace o chybě, modul runtime vyplní mnoho vlastností výjimky s výchozími hodnotami.  
  
 Jestliže metoda selže v nespravovaném kódu, může být předán segment spravovaný kód výjimky. Téma [výsledků HRESULT a výjimek](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) obsahuje tabulku, která ukazuje, jak HRESULTS mapují na objekty výjimek modulu runtime.  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
