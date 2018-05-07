---
title: Funkce zpětného volání
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4494eda29ca6065a157869ec2f93b4875391824
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="callback-functions"></a>Funkce zpětného volání
Funkce zpětného volání je kód v rámci spravované aplikace, která pomáhá nespravované funkce DLL dokončení úkolu. Volání funkce zpětného volání předat nepřímo ze spravované aplikace, prostřednictvím funkce knihovny DLL a zpět do spravované implementace. Některé z mnoha funkcí knihovny DLL volána s platformou vyvolání vyžadují funkce zpětného volání ve spravovaném kódu správně spouštět.  
  
 K volání většinu funkcí knihovny DLL ze spravovaného kódu, vytvořte spravované definici funkce a poté ji volat. Proces je jednoduchý.  
  
 Pomocí funkce knihovny DLL, která vyžaduje funkci zpětného volání má některé další kroky. Nejdřív musí určit, zda funkce vyžaduje zpětné volání prohlížením v dokumentaci pro funkci. Dále je nutné vytvořit funkce zpětného volání ve spravované aplikaci. Nakonec můžete volat funkce DLL předávání ukazatel do funkce zpětného volání jako argument. Na následujícím obrázku jsou shrnuté tyto kroky.  
  
 ![Vyvolání platformy zpětného volání](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")  
Funkce zpětného volání a implementace  
  
 Funkce zpětného volání jsou ideální pro použití v situacích, ve kterých se úloha provádí opakovaně. Další běžné využití je s výčet funkcí, jako **EnumFontFamilies**, **EnumPrinters**, a **EnumWindows** v rozhraní API Win32. **EnumWindows** funkce zobrazí prostřednictvím všechny existující windows v počítači, volání funkce zpětného volání provést úlohu, u všech oken. Pokyny a příklady naleznete v tématu [postupy: implementace funkcí zpětného volání](../../../docs/framework/interop/how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Implementace funkcí zpětného volání](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
