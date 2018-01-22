---
title: "Aspekty hostování ovládacího prvku ActiveX ve formuláři Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23c8476e4013cca6d906d85f11658deddc585869
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Aspekty hostování ovládacího prvku ActiveX ve formuláři Windows
I když Windows Forms jsou optimalizovány na hostitele Windows Forms – ovládací prvky, můžete dál používat ovládací prvky ActiveX. Při plánování aplikace, která používá ovládací prvky ActiveX, mít na paměti následující aspekty:  
  
-   **Zabezpečení** modul common language runtime se rozšířily s ohledem na zabezpečení přístupu kódu. U aplikací s Windows Forms můžete spustit v plně důvěryhodný pro prostředí bez problém a v případě polovičním důvěryhodného prostředí s většinou funkcí, které jsou dostupné. Ovládací prvky Windows Forms může být hostovaný v prohlížeči se žádné komplikace. V rozhraní Windows Forms – ovládací prvky ActiveX nelze však využít výhod těchto vylepšení zabezpečení. Používání ovládacího prvku ActiveX vyžaduje oprávnění nespravovaného kódu, který je nastaven s <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> vlastnost. Další informace o zabezpečení a oprávnění nespravovaného kódu najdete v tématu <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
-   **Celkové náklady na vlastnictví** ovládací prvky ActiveX přidán do formuláře Windows jsou nasazeny pomocí tohoto formuláře Windows jako celek, které můžete přidat výrazně velikost souborů vytvořit. Použití ovládacích prvků ActiveX v rozhraní Windows Forms navíc vyžaduje zápis do registru. To je na počítači uživatele než ovládací prvky Windows Forms, které se to nevyžaduje.  
  
    > [!NOTE]
    >  Práce s prvku ActiveX ovládacího prvku vyžaduje použití Obálka zprostředkovatele komunikace s objekty COM. Další informace najdete v tématu [interoperabilita modelů COM v jazyce Visual Basic a Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    >  Pokud název člena ovládacího prvku ActiveX odpovídá názvu definované v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], pak bude import ovládacích prvků ActiveX předpony název člena s **Ctl** při vytvoří <xref:System.Windows.Forms.AxHost> odvozené třídy. Například, pokud má vlastní ovládací prvek ActiveX člen s názvem **rozložení**, bude přejmenován **CtlLayout** ve třídě odvozené AxHost protože **rozložení** událost je definována v rámci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md)  
 [Ovládací prvky a programovatelný objekty porovnání v různých jazycích a knihovny](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Vkládání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)
