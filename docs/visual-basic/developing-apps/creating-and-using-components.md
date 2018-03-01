---
title: "Vytváření a používání součástí v jazyce Visual Basic"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 17c9b7440d60c38ba30d230f8412c3ca1a21830a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-and-using-components-in-visual-basic"></a>Vytváření a používání součástí v jazyce Visual Basic
A *součást* je třída, která implementuje <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> rozhraní nebo která pochází přímo nebo nepřímo z třídu, která implementuje <xref:System.ComponentModel.IComponent>. A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] součást je objekt, který je opakovaně použitelný, můžete spolupracovat s ostatními objekty a umožňuje řídit externí zdroje a podpora návrhu.  
  
 Důležitou součást součástí je, že jsou navrhovatelé, což znamená, že v můžete použít třídu, která je součástí [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrované vývojové prostředí. Součást můžete přidat do sady nástrojů, přetáhnout a do formuláře a s nimi manipulovat, pokud na návrhovou plochu. Všimněte si, že základní podpora návrhu pro součásti je integrovaná do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; vývojář součástí nemá žádné další práci využívat základní funkce návrhu.  
  
 A *řízení* je podobná komponentu, oba jsou navrhovatelé. Však ovládacího prvku poskytuje uživatelské rozhraní, zatímco součást neexistuje. Ovládací prvek musí být odvozeny od jednu z tříd základního ovládacího prvku: <xref:System.Windows.Forms.Control> nebo <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Kdy vytvořit komponentu  
 Pokud se budou používat vlastní třídy v návrh prostor (třeba Windows Forms nebo Návrhář webových formulářů), ale nemá žádné uživatelské rozhraní, měl by být komponenta a implementovat <xref:System.ComponentModel.IComponent>, nebo je odvozena od třídy, který implementuje přímo nebo nepřímo <xref:System.ComponentModel.IComponent>.  
  
 <xref:System.ComponentModel.Component> a <xref:System.ComponentModel.MarshalByValueComponent> třídy jsou základní implementací <xref:System.ComponentModel.IComponent> rozhraní. Hlavní rozdíl mezi tyto třídy je, že <xref:System.ComponentModel.Component> třída je zařazena pomocí odkazu, zatímco <xref:System.ComponentModel.IComponent> je zařazena pomocí hodnoty. Následující seznam obsahuje obecné pokyny pro implementátory informačních technologií.  
  
-   Pokud příslušné součásti musí být zařazena pomocí odkazu, odvozena od <xref:System.ComponentModel.Component>.  
  
-   Pokud příslušné součásti musí být zařazena pomocí hodnoty, odvozena od <xref:System.ComponentModel.MarshalByValueComponent>.  
  
-   Pokud příslušné součásti nelze odvodit z jedné ze základních implementací kvůli jedné dědičnosti, implementujte <xref:System.ComponentModel.IComponent>.  
  
## <a name="component-classes"></a>Třídy komponent  
 <xref:System.ComponentModel> Obor názvů obsahuje třídy, které se používají k implementaci chování za běhu a návrhu součásti a ovládacích prvků. Tento obor názvů obsahuje základní třídy a rozhraní pro implementace atributů, převaděčů typů vazeb na zdroje dat a licencování součásti.  
  
 Základní třídy komponenty jsou:  
  
-   <xref:System.ComponentModel.Component>. Základní implementace pro <xref:System.ComponentModel.IComponent> rozhraní. Tato třída umožňuje objekt sdílení mezi aplikacemi.  
  
-   <xref:System.ComponentModel.MarshalByValueComponent>. Základní implementace pro <xref:System.ComponentModel.IComponent> rozhraní.  
  
-   <xref:System.ComponentModel.Container>. Základní implementace pro <xref:System.ComponentModel.IContainer> rozhraní. Tato třída zapouzdří nula nebo více součástí.  
  
 Třídy používané pro licencování komponenty jsou:  
  
-   <xref:System.ComponentModel.License>. Abstraktní základní třída pro všechny licence. Licence je udělit konkrétní instanci součásti.  
  
-   <xref:System.ComponentModel.LicenseManager>. Poskytuje vlastnosti a metody pro přidání do komponenty licenci a ke správě <xref:System.ComponentModel.LicenseProvider>.  
  
-   <xref:System.ComponentModel.LicenseProvider>. Abstraktní základní třída pro implementaci zprostředkovatele licence.  
  
-   <xref:System.ComponentModel.LicenseProviderAttribute>. Určuje, <xref:System.ComponentModel.LicenseProvider> třídu se má použít s třídou.  
  
 Třídy běžně používané pro popis a uchování součásti.  
  
-   <xref:System.ComponentModel.TypeDescriptor>. Poskytuje informace o vlastnostech pro komponentu, například jeho atributy, vlastnosti a události.  
  
-   <xref:System.ComponentModel.EventDescriptor>. Poskytuje informace o události.  
  
-   <xref:System.ComponentModel.PropertyDescriptor>. Poskytuje informace o vlastnosti.  
  
## <a name="related-sections"></a>Související oddíly  
 [Řešení potíží s vytvářením ovládacích prvků a komponent](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Vysvětluje, jak opravit běžné problémy.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přístup k podpoře návrhu v systému Windows Forms](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 
