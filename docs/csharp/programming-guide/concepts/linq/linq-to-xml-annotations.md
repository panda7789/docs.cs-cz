---
title: Poznámky v LINQ to XML
description: Naučte se používat poznámky v LINQ to XML k přidružení libovolných libovolných objektů libovolného typu k libovolné komponentě XML ve stromu XML.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: e7da666139c10b26de37816693202d96498f52d8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165575"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="eefc6-103">Poznámky v LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="eefc6-103">LINQ to XML Annotations</span></span>

<span data-ttu-id="eefc6-104">Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňují přidružit libovolný libovolný objekt libovolného typu k libovolné komponentě XML ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="eefc6-104">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="eefc6-105">Chcete-li přidat anotaci do komponenty XML, jako je například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> , zavoláte <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="eefc6-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="eefc6-106">Poznámky načtete podle typu.</span><span class="sxs-lookup"><span data-stu-id="eefc6-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="eefc6-107">Všimněte si, že poznámky nejsou součástí informační sady XML. nejsou serializovány nebo deserializovány.</span><span class="sxs-lookup"><span data-stu-id="eefc6-107">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="eefc6-108">Metody</span><span class="sxs-lookup"><span data-stu-id="eefc6-108">Methods</span></span>

<span data-ttu-id="eefc6-109">Při práci s poznámkami můžete použít následující metody:</span><span class="sxs-lookup"><span data-stu-id="eefc6-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="eefc6-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="eefc6-110">Method</span></span>|<span data-ttu-id="eefc6-111">Popis</span><span class="sxs-lookup"><span data-stu-id="eefc6-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="eefc6-112">Přidá objekt do seznamu poznámek <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="eefc6-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="eefc6-113">Získá první objekt poznámky zadaného typu z <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="eefc6-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="eefc6-114">Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="eefc6-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="eefc6-115">Odstraní poznámky zadaného typu z <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="eefc6-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
