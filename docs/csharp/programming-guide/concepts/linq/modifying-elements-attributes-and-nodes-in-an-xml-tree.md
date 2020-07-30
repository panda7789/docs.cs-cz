---
title: Změna elementů, atributů a uzlů ve stromu XML
description: Další informace o metodách a vlastnostech, které lze použít pro úpravu prvku, jeho podřízených uzlů nebo jeho atributů.
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: bfff882dc57a4f6f4b228563ac923122097d88d0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303163"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Změna elementů, atributů a uzlů ve stromu XML
Následující tabulka shrnuje metody a vlastnosti, které lze použít pro úpravu prvku, jeho podřízených prvků nebo jeho atributů.  
  
 Následující metody upravují <xref:System.Xml.Linq.XElement> .  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Nahradí element pomocí analyzovaného kódu XML.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Odebere veškerý obsah (podřízené uzly a atributy) elementu.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Odebere atributy elementu.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Nahradí veškerý obsah (podřízené uzly a atributy) elementu.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Nahradí atributy elementu.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Nastaví hodnotu atributu. Vytvoří atribut, pokud neexistuje. Pokud je hodnota nastavena na `null` , odebere atribut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Nastaví hodnotu podřízeného prvku. Vytvoří prvek, pokud neexistuje. Pokud je hodnota nastavena na `null` , odebere prvek.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Nahradí obsah (podřízené uzly) prvku zadaným textem.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Nastaví hodnotu prvku.|  
  
 Následující metody upravují <xref:System.Xml.Linq.XAttribute> .  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Nastaví hodnotu atributu.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Nastaví hodnotu atributu.|  
  
 Následující metody upravují <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> ).  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Nahradí uzel novým obsahem.|  
  
 Následující metody upravují <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> ).  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Nahradí podřízené uzly novým obsahem.|  
