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
ms.openlocfilehash: babae31a3be9775d07ca84c54e1177d297cab5cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108755"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Aspekty hostování ovládacího prvku ActiveX ve formuláři Windows
Přestože Windows Forms jsou optimalizované pro hostitelské ovládací prvky Windows Forms, je možné použít ovládací prvky ActiveX. Při plánování aplikaci používá ovládací prvky ActiveX, mít na paměti následující aspekty:  
  
-   **Zabezpečení** vylepšili jsme modul common language runtime s ohledem na zabezpečení přístupu kódu. Aplikace s Windows Forms lze spustit v plně důvěryhodném prostředí bez problému a v částečně důvěryhodném prostředí s většinou funkcí, které jsou přístupné. Ovládací prvky Windows Forms je možné hostovat v prohlížeči se žádná komplikací. Ovládací prvky ActiveX v modelu Windows Forms však nelze využít výhod těchto vylepšení zabezpečení. Používání ovládacího prvku ActiveX vyžaduje oprávnění nespravovaného kódu, který je nastavený s <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> vlastnost. Další informace o zabezpečení a oprávnění nespravovaného kódu, naleznete v tématu <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
-   **Celkové náklady na vlastnictví** přidán do formuláře Windows – ovládací prvky ActiveX jsou nasazeny pomocí formuláře Windows v plné výši, které můžete přidat výrazně velikosti souborů vytvořené. Použití ovládacích prvků ActiveX do formulářů Windows navíc vyžaduje zápis do registru. Toto je na počítači uživatele invazivnější než ovládacích prvků Windows Forms, které nevyžadují, aby to.  
  
    > [!NOTE]
    >  Práce s prvku ActiveX ovládací prvek vyžaduje použití obálku vzájemné spolupráce COM. Další informace najdete v tématu [interoperabilita modelů COM v jazyce Visual Basic a Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    >  Pokud název členu ovládacího prvku ActiveX odpovídá názvu definovanému v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], pak bude k názvu člena přidat předponu Importér ovládacích prvků ActiveX **Ctl** když vytvoří <xref:System.Windows.Forms.AxHost> odvozené třídy. Například, pokud ovládací prvek ActiveX má člen nazvaný **rozložení**, bude přejmenován **CtlLayout** ve třídě AxHost odvozené protože **rozložení** událost je definována v rámci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Zabezpečení přístupu kódu](../../misc/code-access-security.md)
- [Porovnání ovládacích prvků a programovatelných objektů v různých jazycích a knihovnách](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Vkládání ovládacích prvků do formulářů Windows](putting-controls-on-windows-forms.md)
- [Ovládací prvky Windows Forms](index.md)
