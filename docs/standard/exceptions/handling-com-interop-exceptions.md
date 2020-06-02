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
ms.openlocfilehash: 9c8eb374058ddbd2ba3d866079f0f40b292b69ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286103"
---
# <a name="handling-com-interop-exceptions"></a>Zpracování výjimek vzájemné spolupráce COM
Spravovaný a nespravovaný kód může spolupracovat na zpracování výjimek. Pokud metoda vyvolá výjimku ve spravovaném kódu, modul CLR (Common Language Runtime) může předat HRESULT objektu COM. Pokud metoda selže v nespravovaném kódu vrácením chyby HRESULT, modul runtime vyvolá výjimku, která může být zachycena spravovaným kódem.  
  
 Modul runtime automaticky mapuje HRESULT z zprostředkovatele komunikace s objekty COM na konkrétnější výjimky. Například E_ACCESSDENIED se bude <xref:System.UnauthorizedAccessException> E_OUTOFMEMORY <xref:System.OutOfMemoryException> a tak dále.  
  
 Pokud je HRESULT vlastní výsledek nebo pokud je neznámý pro modul runtime, modul runtime předá <xref:System.Runtime.InteropServices.COMException> klientovi Obecné. Vlastnost **ErrorCode** třídy **COMEXCEPTION** obsahuje hodnotu HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Práce s IErrorInfo  
 Pokud je předána chyba z modelu COM do spravovaného kódu, modul runtime naplní objekt výjimky informacemi o chybě. Objekty modelu COM, které podporují IErrorInfo a vracejí hodnoty HRESULT, poskytují tyto informace pro výjimky spravovaného kódu. Například modul runtime mapuje popis z chyby COM na <xref:System.Exception.Message%2A> vlastnost výjimky. Pokud HRESULT neposkytuje žádné další informace o chybě, modul runtime vyplní mnoho vlastností výjimky výchozími hodnotami.  
  
 Pokud metoda v nespravovaném kódu dojde k chybě, může být výjimka předána spravovanému segmentu kódu. Téma [HRESULTS a Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) obsahuje tabulku, která ukazuje, jak jsou HRESULTS mapovány na objekty výjimek za běhu.  

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
