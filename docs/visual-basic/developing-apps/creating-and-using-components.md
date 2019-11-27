---
title: Vytváření a používání komponent
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: 2fefdff9dc27915066e3d92efd8439adffed9fc5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330300"
---
# <a name="creating-and-using-components-in-visual-basic"></a>Vytváření a používání součástí v jazyce Visual Basic

*Komponenta* je třída, která implementuje rozhraní <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> nebo která je odvozena přímo nebo nepřímo ze třídy, která implementuje <xref:System.ComponentModel.IComponent>. Komponenta .NET Framework je objekt, který lze opakovaně použít, může komunikovat s ostatními objekty a poskytuje kontrolu nad externími prostředky a podporou v době návrhu.  
  
 Důležitou funkcí komponent je, že mohou být navržené, což znamená, že třída, která je komponentou, může být použita v integrovaném vývojovém prostředí sady Visual Studio. Komponentu lze přidat do sady nástrojů, přetáhnout ji do formuláře a manipulovat na návrhové ploše. Všimněte si, že základní podpora pro součásti v době návrhu je integrovaná do .NET Framework; Vývojář komponent nemusí provádět žádnou další práci, aby mohl využívat základní funkce pro dobu návrhu.  
  
 *Ovládací prvek* je podobný komponentě, protože obě jsou navržené. Ovládací prvek však poskytuje uživatelské rozhraní, zatímco komponenta nikoli. Ovládací prvek musí být odvozen od jedné ze základních tříd ovládacích prvků: <xref:System.Windows.Forms.Control> nebo <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Kdy vytvořit komponentu  

 Pokud bude vaše třída použita na návrhové ploše (například model Windows Forms nebo Návrhář webových formulářů), ale nemá žádné uživatelské rozhraní, měla by být součástí a implementovat <xref:System.ComponentModel.IComponent>, nebo musí být odvozena od třídy, která přímo nebo nepřímo implementuje <xref:System.ComponentModel.IComponent>.  
  
 Třídy <xref:System.ComponentModel.Component> a <xref:System.ComponentModel.MarshalByValueComponent> jsou základními implementacemi rozhraní <xref:System.ComponentModel.IComponent>. Hlavním rozdílem mezi těmito třídami je, že třída <xref:System.ComponentModel.Component> je zařazena odkazem, zatímco <xref:System.ComponentModel.IComponent> je zařazena podle hodnoty. Následující seznam poskytuje široké pokyny pro implementátory.  
  
- Pokud vaše komponenta musí být zařazená odkazem, odvodit z <xref:System.ComponentModel.Component>.  
  
- Pokud vaše komponenta musí být zařazena podle hodnoty, odvodit z <xref:System.ComponentModel.MarshalByValueComponent>.  
  
- Pokud vaše komponenta nemůže být odvozena z jedné základní implementace z důvodu jedné dědičnosti, implementujte <xref:System.ComponentModel.IComponent>.  
  
## <a name="component-classes"></a>Třídy komponent  

 Obor názvů <xref:System.ComponentModel> poskytuje třídy, které slouží k implementaci chování komponent a ovládacích prvků za běhu a při návrhu. Tento obor názvů zahrnuje základní třídy a rozhraní pro implementaci atributů a převaděčů typů, vázání na zdroje dat a součásti licencování.  
  
 Základní třídy komponenty jsou:  
  
- <xref:System.ComponentModel.Component>. Základní implementace rozhraní <xref:System.ComponentModel.IComponent>. Tato třída umožňuje sdílení objektů mezi aplikacemi.  
  
- <xref:System.ComponentModel.MarshalByValueComponent>. Základní implementace rozhraní <xref:System.ComponentModel.IComponent>.  
  
- <xref:System.ComponentModel.Container>. Základní implementace rozhraní <xref:System.ComponentModel.IContainer>. Tato třída zapouzdřuje nula nebo více součástí.  
  
 Mezi třídy používané při licencování komponent patří:  
  
- <xref:System.ComponentModel.License>. Abstraktní základní třída pro všechny licence Licence je udělena konkrétní instanci komponenty.  
  
- <xref:System.ComponentModel.LicenseManager>. Poskytuje vlastnosti a metody pro přidání licence k komponentě a ke správě <xref:System.ComponentModel.LicenseProvider>.  
  
- <xref:System.ComponentModel.LicenseProvider>. Abstraktní základní třída pro implementaci poskytovatele licencí.  
  
- <xref:System.ComponentModel.LicenseProviderAttribute>. Určuje třídu <xref:System.ComponentModel.LicenseProvider>, která se má použít s třídou.  
  
 Třídy, které se běžně používají pro popis a trvalé komponenty.  
  
- <xref:System.ComponentModel.TypeDescriptor>. Poskytuje informace o vlastnostech součásti, jako jsou atributy, vlastnosti a události.  
  
- <xref:System.ComponentModel.EventDescriptor>. Poskytuje informace o události.  
  
- <xref:System.ComponentModel.PropertyDescriptor>. Poskytuje informace o vlastnosti.  
  
## <a name="related-sections"></a>Související oddíly  

 [Řešení potíží s vytvářením ovládacích prvků a komponent](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Vysvětluje, jak řešit běžné problémy.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: přístup k podpoře v době návrhu v model Windows Forms](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
