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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708929"
---
# <a name="handling-com-interop-exceptions"></a>Zpracování výjimek vzájemné spolupráce COM
Spravovaný a nespravovaný kód může spolupracovat na zpracování výjimek. Pokud metoda vyvolá výjimku ve spravovaném kódu, modul CLR (Common Language Runtime) může předat HRESULT objektu COM. Pokud metoda selže v nespravovaném kódu vrácením chyby HRESULT, modul runtime vyvolá výjimku, která může být zachycena spravovaným kódem.  
  
 Modul runtime automaticky mapuje HRESULT z zprostředkovatele komunikace s objekty COM na konkrétnější výjimky. Například E_ACCESSDENIED se bude <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY se <xref:System.OutOfMemoryException>a tak dále.  
  
 Pokud je HRESULT vlastní výsledek nebo pokud je neznámý pro modul runtime, modul runtime předá klientovi obecný <xref:System.Runtime.InteropServices.COMException>. Vlastnost **ErrorCode** třídy **COMEXCEPTION** obsahuje hodnotu HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Práce s IErrorInfo  
 Pokud je předána chyba z modelu COM do spravovaného kódu, modul runtime naplní objekt výjimky informacemi o chybě. Objekty modelu COM, které podporují IErrorInfo a vracejí hodnoty HRESULT, poskytují tyto informace pro výjimky spravovaného kódu. Modul runtime například mapuje popis z chyby COM na vlastnost <xref:System.Exception.Message%2A> výjimky. Pokud HRESULT neposkytuje žádné další informace o chybě, modul runtime vyplní mnoho vlastností výjimky výchozími hodnotami.  
  
 Pokud metoda v nespravovaném kódu dojde k chybě, může být výjimka předána spravovanému segmentu kódu. Téma [HRESULTS a Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) obsahuje tabulku, která ukazuje, jak jsou HRESULTS mapovány na objekty výjimek za běhu.  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
