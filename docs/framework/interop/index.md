---
title: Spolupráce s nespravovaným kódem
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: edec95ea729fdf26e384b6658c241ca307e60851
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643111"
---
# <a name="interoperating-with-unmanaged-code"></a>Spolupráce s nespravovaným kódem

Rozhraní .NET Framework podporuje interakci s modelu COM komponenty modelu COM + služby, externí knihovny typů a řadě služeb operačního systému. Datové typy, podpisy metod a mechanismy zpracování chyb se liší mezi spravovanými a nespravovanými objektové modely. Pro zjednodušení spolupráce mezi komponenty rozhraní .NET Framework a nespravovaný kód a k usnadnění cesty migrace z klientů i serverů rozdíly mezi tyto modely objektů ukrývá modul common language runtime.

Kód, který spouští pod kontrolou modulu runtime se nazývá spravovaný kód. Kód, který běží mimo modul runtime a naopak, se nazývá nespravovaného kódu. Komponenty modelu COM, ActiveX rozhraní a funkcí rozhraní API Windows jsou příkladem nespravovaného kódu.

## <a name="in-this-section"></a>V tomto oddílu

[Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)  
Popisuje způsob použití komponent modelu COM z aplikace rozhraní .NET Framework.

[Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)  
Popisuje způsob použití součásti rozhraní .NET Framework z aplikace modelu COM.

[Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)  
Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.

[Zařazování spolupráce](interop-marshaling.md)  
Popisuje zařazování pro zprostředkovatele komunikace s objekty COM a platformu vyvolání.

[Postupy: Mapování výsledků HRESULT a výjimek](how-to-map-hresults-and-exceptions.md)  
Popisuje mapování mezi výjimky a HRESULT.

[COM – obálky](com-wrappers.md)  
Popisuje obálky poskytované komunikace s objekty COM.

[Ekvivalence typů a vestavěné typy spolupráce](type-equivalence-and-embedded-interop-types.md)  
Popisuje, jak se vloží informace o typu pro typy modelu COM v sestaveních a jak určuje ekvivalence vestavěné typy modelu COM, modul common language runtime.

[Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Popisuje, jak vytvořit primární sestavení vzájemné spolupráce pomocí *Tlbimp.exe* (Importér knihovny typů).

[Postupy: Registrace primárních sestavení spolupráce](how-to-register-primary-interop-assemblies.md)  
Popisuje postup registrace primárních sestavení spolupráce, než je můžete odkazovat ve svých projektech.

[Bezregistrační zprostředkovatel komunikace s objekty COM](registration-free-com-interop.md)  
Popisuje, jak komunikace s objekty COM se může aktivovat komponenty bez pomocí registru Windows.

[Postupy: Konfigurace Bezregistrační aktivace komponent COM založené na platformě .NET](configure-net-framework-based-com-components-for-reg.md)  
Popisuje, jak vytvořit manifest aplikace a jak vytvořit a vložení manifestu do komponenty.
