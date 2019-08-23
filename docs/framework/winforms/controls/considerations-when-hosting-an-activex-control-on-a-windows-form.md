---
title: Aspekty hostování ovládacího prvku ActiveX ve formuláři Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: 0b95bab20299b966b9f3c6e6ce089a641670f974
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933415"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Aspekty hostování ovládacího prvku ActiveX ve formuláři Windows
I když model Windows Forms byly optimalizované pro hostování model Windows Formsch ovládacích prvků, můžete i nadále používat ovládací prvky ActiveX. Při plánování aplikace, která používá ovládací prvky ActiveX, mějte na paměti následující skutečnosti:  
  
- **Zabezpečení** Modul CLR (Common Language Runtime) byl vylepšený s ohledem na zabezpečení přístupu kódu. Aplikace, které používají model Windows Forms, můžou běžet v plně důvěryhodném prostředí bez problémů a v částečně důvěryhodném prostředí s využitím většiny dostupných funkcí. Ovládací prvky model Windows Forms můžou být hostované v prohlížeči bez komplikací. Ovládací prvky ActiveX v model Windows Forms ale nemůžou využít tato vylepšení zabezpečení. Spuštění ovládacího prvku ActiveX vyžaduje oprávnění nespravovaného kódu, které je nastaveno <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> pomocí vlastnosti. Další informace o oprávnění zabezpečení a nespravovaného kódu naleznete <xref:System.Security.Permissions.SecurityPermissionAttribute>v tématu.  
  
- **Celkové náklady na vlastnictví** Ovládací prvky ActiveX přidané do formuláře Windows jsou nasazeny s tímto formulářem systému Windows v celém rozsahu, což může významně přidat velikost souborů, které byly vytvořeny. Kromě toho použití ovládacích prvků ActiveX v model Windows Forms vyžaduje zápis do registru. To je více invazivní pro počítač uživatele než model Windows Forms ovládací prvky, které to nevyžadují.  
  
    > [!NOTE]
    > Práce s ovládacím prvkem ActiveX vyžaduje použití obálky zprostředkovatele komunikace s objekty COM. Další informace najdete v tématu [interoperabilita modelu COM v Visual Basic C#a vizuálu ](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    > Pokud název členu ovládacího prvku ActiveX odpovídá názvu definovanému v .NET Framework, pak Nástroj pro import ovládacího prvku ActiveX při vytváření <xref:System.Windows.Forms.AxHost> odvozené třídy nastaví předponu názvu člena pomocí **seznamu CTL** . Například pokud má ovládací prvek ActiveX člena s názvem **layout**, je přejmenován **CtlLayout** v odvozené třídě AxHost, protože událost **Layout** je definována v rámci .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přidat ovládací prvky ActiveX do model Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Zabezpečení přístupu kódu](../../misc/code-access-security.md)
- [Ovládací prvky a programovatelné objekty v porovnání s různými jazyky a knihovnami](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Vkládání ovládacích prvků do Windows Forms](putting-controls-on-windows-forms.md)
- [Windows Forms – ovládací prvky](index.md)
