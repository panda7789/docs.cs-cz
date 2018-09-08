---
title: Použití manipulace a nečinnosti v aplikaci XNA
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44134620"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a>Použití manipulace a nečinnosti v aplikaci XNA
Tento článek popisuje, jak řídit přesun kameny můžete manipulace a nečinnosti v aplikaci Microsoft XNA zpracování. Předtím, než se pustíte do čtení tohoto článku, měli byste se seznámit s [přehled manipulace a nečinnosti](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tématu a znáte základní koncepty programování XNA.  
  
 K provedení úloh popsaných v tomto článku, váš projekt XNA musí odkazovat <xref:System.Windows.Input.Manipulations> sestavení a musí mít [sadu XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([Stáhnout](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) nainstalovaný ve vašem počítači tak vaše Projekt může odkazovat na sestavení XNA.  
  
## <a name="overview-of-functionality"></a>Přehled funkcí  
 V tomto článku se dozvíte, jak vytvořit vlastní třídu, která představuje her část, která používá manipulace a nečinnost zpracování. Tato třída umožňuje manipulaci s her napříč obrazovkou pomocí přetahování myší a pak uvolníte. Po vydání nečinnost zpracování udržuje her část, protože postupný přechod může zpomalit. Přesun je lineární a angular.  
  
 ![Jednoduchý manipulace a nečinnost aplikace. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")  
  
 Kromě toho se vytvoří vlastní kolekce, která spravuje her na více místech. Tato funkce usnadňuje zpracování, které je nutné ze třídy přenos hry XNA.  
  
 [Vytvoření třídy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [Vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Vytvoření třídy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Výpis úplného kódu](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.Manipulations>  
 [Přehled manipulace a nečinnosti](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
