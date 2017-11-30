---
title: "Použití manipulace a nečinnosti v aplikaci XNA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: adf48310c1c2e0c59224ab820211e818a2401579
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a>Použití manipulace a nečinnosti v aplikaci XNA
Tento článek popisuje, jak můžete použít manipulace a nečinnosti zpracování v aplikaci Microsoft XNA ovládat pohyb herní částí. Předtím, než se pustíte do čtení tohoto článku, měli byste se seznámit s [přehled manipulace a nečinnosti](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tématu a znát základní XNA koncepce programování.  
  
 Úkoly popsané v tomto článku projektu XNA musí odkazovat <xref:System.Windows.Input.Manipulations> sestavení a musí mít [XNA herní Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([Stáhnout](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) v počítači nainstalován, který vaše Projekt může odkazovat XNA sestavení.  
  
## <a name="overview-of-functionality"></a>Přehled funkcí  
 Tento článek ukazuje, jak vytvořit vlastní třídu, která představuje herní část, která používá manipulace a nečinnosti zpracování. Tato třída umožňuje manipulaci s herní po obrazovce pomocí přetahování myší a pak ho uvolněním. Po vydání, nečinnosti zpracování udržuje herní část postupný přechod jak zpomalí. Pohyb je lineární a úhlová.  
  
 ![Jednoduchý manipulace a nečinnosti aplikace. ] (../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")  
  
 Kromě toho je vytvořen vlastní kolekce, který spravuje herní na více místech. Tato funkce zjednodušuje zpracování požadované ze třídy XNA hra.  
  
 [Vytvoření třídy Gamepiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [Vytvoření třídy Gamepiececollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Vytvoření třídy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Výpis úplného kódu](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.Manipulations>  
 [Přehled manipulace a nečinnosti](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
