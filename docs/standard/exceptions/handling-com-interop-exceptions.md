---
title: "Zpracování výjimek vzájemné spolupráce COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e894d07e77b929b1ea22df2d34e542544ec3b1f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
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
