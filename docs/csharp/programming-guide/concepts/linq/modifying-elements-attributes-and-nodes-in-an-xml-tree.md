---
title: Úprava prvků, atributů a uzlů ve stromu XML3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484229"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Změna elementů, atributů a uzlů ve stromu XML
Následující tabulka shrnuje metody a vlastnosti, které můžete použít k úpravě prvku, jeho podřízených prvků nebo jeho atributů.  
  
 Následující metody upravují . <xref:System.Xml.Linq.XElement>  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Nahradí prvek analyzovaným XML.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Odebere veškerý obsah (podřízené uzly a atributy) prvku.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Odebere atributy prvku.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Nahradí veškerý obsah (podřízené uzly a atributy) prvku.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Nahradí atributy prvku.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Nastaví hodnotu atributu. Vytvoří atribut, pokud neexistuje. Pokud je hodnota `null`nastavena na , odebere atribut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Nastaví hodnotu podřízeného prvku. Vytvoří prvek, pokud neexistuje. Pokud je hodnota `null`nastavena na , odebere prvek.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Nahradí obsah (podřízené uzly) prvku zadaným textem.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Nastaví hodnotu prvku.|  
  
 Následující metody upravují . <xref:System.Xml.Linq.XAttribute>  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Nastaví hodnotu atributu.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Nastaví hodnotu atributu.|  
  
 Následující metody upravují <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XElement> (včetně nebo). <xref:System.Xml.Linq.XDocument>  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Nahradí uzel novým obsahem.|  
  
 Následující metody <xref:System.Xml.Linq.XContainer> upravují <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>(nebo).  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Nahradí podřízené uzly novým obsahem.|  
