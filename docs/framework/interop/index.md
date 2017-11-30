---
title: "Spolupráce s nespravovaným kódem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2db5b8c2425637e24086f54e8ef69b0e5aac3633
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interoperating-with-unmanaged-code"></a>Spolupráce s nespravovaným kódem
Rozhraní .NET Framework zvýší úroveň interakci s COM komponenty modelu COM + služby, knihovny externích typů a mnoho služeb operačního systému. Datové typy, metoda podpisy a zpracování chyb mechanismy liší mezi spravovanými a nespravovanými objektové modely. Pro zjednodušení vzájemná spolupráce mezi součástmi rozhraní .NET Framework a nespravovaného kódu a usnadňují cesty migrace, modul common language runtime ukrývá od klientů a serverů rozdíly v těchto modelů objektu.  
  
 Kód, který spouští pod kontrolou modulu runtime nazývá spravovaného kódu. Kód, který je spuštěn mimo modul runtime naopak se nazývá nespravovaného kódu. COM – součásti ActiveX rozhraní a funkcí rozhraní API Win32 jsou příklady nespravovaného kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Spolupráce s nespravovaným kódem postupy](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 Obsahuje odkazy na všechny postupy v rámcová dokumentace pro spolupráce s nespravovaným kódem.  
  
 [Vystavení součástí COM v rozhraní .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 Popisuje, jak komponenty modelu COM v aplikacích rozhraní .NET Framework.  
  
 [Vystavení součástí .NET Framework do modelu COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Popisuje způsob použití součásti rozhraní .NET Framework z aplikace modelu COM.  
  
 [Používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.  
  
 [Aspekty návrhu pro spolupráci](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 Poskytuje tipy pro zápis integrované COM – součásti.  
  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)  
 Popisuje zařazování pro vyvolání zprostředkovatel komunikace s objekty COM a platformu.  
  
 [Postupy: mapování výsledků HRESULT a výjimek](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 Popisuje mapování mezi výjimky a jejich hodnoty HRESULT.  
  
 [Spolupráce pomocí obecných typů](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 Popisuje chování při použití v zprostředkovatel komunikace s objekty COM – obecné typy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Interoperabilita modelů COM Upřesnit](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Obsahuje odkazy na další informace o zahrnutí komponenty modelu COM do své aplikace rozhraní .NET Framework.
