---
title: Vytváření a používání součástí v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: ca336e2ffa3831167088d92bfca017ce2226d8a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014320"
---
# <a name="creating-and-using-components-in-visual-basic"></a>Vytváření a používání součástí v jazyce Visual Basic
A *komponenty* je třída, která implementuje <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> rozhraní nebo že odvozený přímo nebo nepřímo ze třídy, která implementuje <xref:System.ComponentModel.IComponent>. A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] součást je objekt, který je opakovaně, může spolupracovat s ostatními objekty a zajišťuje kontrolu nad externím prostředkům a podpory během návrhu.  
  
 Důležitou funkcí komponent je, že jsou navrhovatelé, což znamená, že třída, která je součástí je možné v aplikaci Visual Studio integrované vývojové prostředí. Komponenty lze přidávat do panelu nástrojů, kvůli usnadnění použití vypsány a do formuláře a manipulovat na návrhové ploše. Všimněte si, že základní podpory během návrhu pro komponenty je integrovaná [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; jako vývojář komponent a není třeba provádět jakékoli další práce, abyste mohli využívat základní funkce návrhu.  
  
 A *ovládací prvek* je podobný komponentu, jak jsou navrhovatelé. Ovládací prvek však poskytuje uživatelské rozhraní, ale součást nikoli. Ovládací prvek musí být odvozen z jedné třídy základních ovládacích prvků: <xref:System.Windows.Forms.Control> nebo <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Kdy vytvořit součást  
 Pokud vaše třída se budou používat v návrhovém povrchu (jako je například Windows Forms nebo Návrhář webových formulářů), ale nemá žádné uživatelské rozhraní, by měla být komponenta a implementovat <xref:System.ComponentModel.IComponent>, nebo jsou odvozeny z třídy, která implementuje přímo nebo nepřímo <xref:System.ComponentModel.IComponent>.  
  
 <xref:System.ComponentModel.Component> a <xref:System.ComponentModel.MarshalByValueComponent> třídy jsou základní implementací <xref:System.ComponentModel.IComponent> rozhraní. Hlavní rozdíl mezi těmito třídami, který je <xref:System.ComponentModel.Component> třídy je zařazen podle odkazu, zatímco <xref:System.ComponentModel.IComponent> je zařazen podle hodnoty. Následující seznam obsahuje širokou pokyny pro vývojáře.  
  
- Pokud vaše komponenta musí být zařazen podle odkazu, jsou odvozeny z <xref:System.ComponentModel.Component>.  
  
- Pokud vaše komponenta je potřeba zařadit hodnotu, odvozujte z <xref:System.ComponentModel.MarshalByValueComponent>.  
  
- Pokud vaše komponenta nelze odvodit z jedné základní implementace kvůli jednoduchá dědičnost, implementovat <xref:System.ComponentModel.IComponent>.  
  
## <a name="component-classes"></a>Třídy komponent  
 <xref:System.ComponentModel> Obor názvů obsahuje třídy, které se používají k implementují chování komponent a ovládacích prvků za běhu a návrhu. Tento obor názvů obsahuje základní třídy a rozhraní pro implementaci atributy a převaděče typů vazeb na zdroje dat a součásti licencování.  
  
 Základní třídy komponent jsou:  
  
- <xref:System.ComponentModel.Component>. Základní implementace pro <xref:System.ComponentModel.IComponent> rozhraní. Tato třída umožňuje objektu sdílení mezi aplikacemi.  
  
- <xref:System.ComponentModel.MarshalByValueComponent>. Základní implementace pro <xref:System.ComponentModel.IComponent> rozhraní.  
  
- <xref:System.ComponentModel.Container>. Základní implementace pro <xref:System.ComponentModel.IContainer> rozhraní. Tato třída zapouzdří nula nebo více komponent.  
  
 Zde jsou některé třídy používané pro licencování součástí:  
  
- <xref:System.ComponentModel.License>. Abstraktní základní třída pro všechny licence. Licence je udělena na konkrétní instanci komponenty.  
  
- <xref:System.ComponentModel.LicenseManager>. Poskytuje vlastnosti a metody, které můžete přidat licenci na komponentu a ke správě <xref:System.ComponentModel.LicenseProvider>.  
  
- <xref:System.ComponentModel.LicenseProvider>. Abstraktní základní třída pro implementaci zprostředkovatele licence.  
  
- <xref:System.ComponentModel.LicenseProviderAttribute>. Určuje, <xref:System.ComponentModel.LicenseProvider> třídu použít s třídou.  
  
 Třídy běžně používané pro popisující a při zachování komponenty.  
  
- <xref:System.ComponentModel.TypeDescriptor>. Obsahuje informace o vlastnostech pro komponentu, jako jsou jeho atributy, vlastnosti a události.  
  
- <xref:System.ComponentModel.EventDescriptor>. Poskytuje informace o události.  
  
- <xref:System.ComponentModel.PropertyDescriptor>. Poskytuje informace o vlastnosti.  
  
## <a name="related-sections"></a>Související oddíly  
 [Řešení potíží s vytvářením ovládacích prvků a komponent](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Vysvětluje, jak řešit běžné potíže.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Podpora návrhu přístupu ve Windows Forms](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
