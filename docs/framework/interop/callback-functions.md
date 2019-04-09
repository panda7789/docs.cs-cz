---
title: Funkce zpětného volání
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65f5e11a8fb40527387c14cdd8dec7f0bfc5c697
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196993"
---
# <a name="callback-functions"></a>Funkce zpětného volání
Funkce zpětného volání je kód v rámci spravované aplikace, která pomáhá nespravovanou funkci knihovny DLL dokončení úkolu. Volání funkce zpětného volání při předání nepřímo z aplikace spravované prostřednictvím funkce knihovny DLL a zpět na spravovanou implementaci. Některé z mnoha funkcí knihovny DLL volána s platformou vyvolat vyžadují funkce zpětného volání ve spravovaném kódu správně spustit.  
  
 Pro volání většinu funkcí knihovny DLL ze spravovaného kódu, vytvoří definici spravované funkce a následně ji zavolat. Proces je jednoduchý.  
  
 Pomocí funkce knihovny DLL, která vyžaduje funkci zpětného volání obsahuje několik dalších kroků. Nejprve musíte určit, jestli funkce vyžaduje zobrazením v dokumentaci pro funkci zpětného volání. V dalším kroku je nutné vytvořit funkci zpětného volání ve spravované aplikaci. Nakonec můžete volat funkce knihovny DLL předání ukazatele na funkci zpětného volání jako argument. 
 
 Následující obrázek obsahuje souhrn zpětného volání funkce a provedení kroků:  
  
 ![Diagram zobrazující platformu vyvolání zpětného volání procesu.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Funkce zpětného volání jsou ideální pro použití v situacích, ve kterých se úloha provádí opakovaně. Jiné běžné použití je výčet funkcí, jako například **EnumFontFamilies**, **EnumPrinters**, a **EnumWindows** v rozhraní Windows API. **EnumWindows** funkce vytvoří výčet prostřednictvím všechny existující windows v počítači, zavoláním funkce zpětného volání k provedení úkolu na každé okno. Pokyny a příklad najdete v tématu [jak: Implementace funkcí zpětného volání](../../../docs/framework/interop/how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Implementace funkcí zpětného volání](../../../docs/framework/interop/how-to-implement-callback-functions.md)
- [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
