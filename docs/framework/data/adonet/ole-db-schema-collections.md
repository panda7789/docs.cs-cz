---
title: "Kolekcemi schémat OLE DB"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33e794559abd7f619f7431683f06e59705b57d41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="17100-102">Kolekcemi schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="17100-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="17100-103">Tato část popisuje podporu kolekci schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="17100-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="17100-104">Zprostředkovatel Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="17100-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="17100-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="17100-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="17100-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="17100-106">Tables</span></span>  
  
-   <span data-ttu-id="17100-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="17100-107">Columns</span></span>  
  
-   <span data-ttu-id="17100-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="17100-108">Procedures</span></span>  
  
-   <span data-ttu-id="17100-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="17100-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="17100-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="17100-110">Catalog</span></span>  
  
-   <span data-ttu-id="17100-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="17100-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="17100-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="17100-112">Tables</span></span>  
  
|<span data-ttu-id="17100-113">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-113">ColumnName</span></span>|<span data-ttu-id="17100-114">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-115">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-116">String</span><span class="sxs-lookup"><span data-stu-id="17100-116">String</span></span>|  
|<span data-ttu-id="17100-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-118">String</span><span class="sxs-lookup"><span data-stu-id="17100-118">String</span></span>|  
|<span data-ttu-id="17100-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-119">TABLE_NAME</span></span>|<span data-ttu-id="17100-120">String</span><span class="sxs-lookup"><span data-stu-id="17100-120">String</span></span>|  
|<span data-ttu-id="17100-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-121">TABLE_TYPE</span></span>|<span data-ttu-id="17100-122">String</span><span class="sxs-lookup"><span data-stu-id="17100-122">String</span></span>|  
|<span data-ttu-id="17100-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-123">TABLE_GUID</span></span>|<span data-ttu-id="17100-124">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-124">Guid</span></span>|  
|<span data-ttu-id="17100-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-125">DESCRIPTION</span></span>|<span data-ttu-id="17100-126">String</span><span class="sxs-lookup"><span data-stu-id="17100-126">String</span></span>|  
|<span data-ttu-id="17100-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-127">TABLE_PROPID</span></span>|<span data-ttu-id="17100-128">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-128">Int64</span></span>|  
|<span data-ttu-id="17100-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="17100-129">DATE_CREATED</span></span>|<span data-ttu-id="17100-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-130">DateTime</span></span>|  
|<span data-ttu-id="17100-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="17100-131">DATE_MODIFIED</span></span>|<span data-ttu-id="17100-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="17100-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="17100-133">Columns</span></span>  
  
|<span data-ttu-id="17100-134">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-134">ColumnName</span></span>|<span data-ttu-id="17100-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-136">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-137">String</span><span class="sxs-lookup"><span data-stu-id="17100-137">String</span></span>|  
|<span data-ttu-id="17100-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-139">String</span><span class="sxs-lookup"><span data-stu-id="17100-139">String</span></span>|  
|<span data-ttu-id="17100-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-140">TABLE_NAME</span></span>|<span data-ttu-id="17100-141">String</span><span class="sxs-lookup"><span data-stu-id="17100-141">String</span></span>|  
|<span data-ttu-id="17100-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-142">COLUMN_NAME</span></span>|<span data-ttu-id="17100-143">String</span><span class="sxs-lookup"><span data-stu-id="17100-143">String</span></span>|  
|<span data-ttu-id="17100-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-144">COLUMN_GUID</span></span>|<span data-ttu-id="17100-145">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-145">Guid</span></span>|  
|<span data-ttu-id="17100-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-146">COLUMN_PROPID</span></span>|<span data-ttu-id="17100-147">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-147">Int64</span></span>|  
|<span data-ttu-id="17100-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="17100-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="17100-149">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-149">Int64</span></span>|  
|<span data-ttu-id="17100-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="17100-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="17100-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-151">Boolean</span></span>|  
|<span data-ttu-id="17100-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="17100-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="17100-153">String</span><span class="sxs-lookup"><span data-stu-id="17100-153">String</span></span>|  
|<span data-ttu-id="17100-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="17100-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="17100-155">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-155">Int64</span></span>|  
|<span data-ttu-id="17100-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="17100-156">IS_NULLABLE</span></span>|<span data-ttu-id="17100-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-157">Boolean</span></span>|  
|<span data-ttu-id="17100-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-158">DATA_TYPE</span></span>|<span data-ttu-id="17100-159">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-159">Int32</span></span>|  
|<span data-ttu-id="17100-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-160">TYPE_GUID</span></span>|<span data-ttu-id="17100-161">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-161">Guid</span></span>|  
|<span data-ttu-id="17100-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="17100-163">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-163">Int64</span></span>|  
|<span data-ttu-id="17100-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="17100-165">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-165">Int64</span></span>|  
|<span data-ttu-id="17100-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="17100-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="17100-167">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-167">Int32</span></span>|  
|<span data-ttu-id="17100-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="17100-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="17100-169">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-169">Int16</span></span>|  
|<span data-ttu-id="17100-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="17100-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="17100-171">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-171">Int64</span></span>|  
|<span data-ttu-id="17100-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="17100-173">String</span><span class="sxs-lookup"><span data-stu-id="17100-173">String</span></span>|  
|<span data-ttu-id="17100-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="17100-175">String</span><span class="sxs-lookup"><span data-stu-id="17100-175">String</span></span>|  
|<span data-ttu-id="17100-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="17100-177">String</span><span class="sxs-lookup"><span data-stu-id="17100-177">String</span></span>|  
|<span data-ttu-id="17100-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="17100-179">String</span><span class="sxs-lookup"><span data-stu-id="17100-179">String</span></span>|  
|<span data-ttu-id="17100-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="17100-181">String</span><span class="sxs-lookup"><span data-stu-id="17100-181">String</span></span>|  
|<span data-ttu-id="17100-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-182">COLLATION_NAME</span></span>|<span data-ttu-id="17100-183">String</span><span class="sxs-lookup"><span data-stu-id="17100-183">String</span></span>|  
|<span data-ttu-id="17100-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="17100-185">String</span><span class="sxs-lookup"><span data-stu-id="17100-185">String</span></span>|  
|<span data-ttu-id="17100-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="17100-187">String</span><span class="sxs-lookup"><span data-stu-id="17100-187">String</span></span>|  
|<span data-ttu-id="17100-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-188">DOMAIN_NAME</span></span>|<span data-ttu-id="17100-189">String</span><span class="sxs-lookup"><span data-stu-id="17100-189">String</span></span>|  
|<span data-ttu-id="17100-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-190">DESCRIPTION</span></span>|<span data-ttu-id="17100-191">String</span><span class="sxs-lookup"><span data-stu-id="17100-191">String</span></span>|  
|<span data-ttu-id="17100-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="17100-192">COLUMN_LCID</span></span>|<span data-ttu-id="17100-193">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-193">Int32</span></span>|  
|<span data-ttu-id="17100-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="17100-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="17100-195">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-195">Int32</span></span>|  
|<span data-ttu-id="17100-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="17100-196">COLUMN_SORTID</span></span>|<span data-ttu-id="17100-197">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-197">Int32</span></span>|  
|<span data-ttu-id="17100-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="17100-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="17100-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="17100-199">Byte[]</span></span>|  
|<span data-ttu-id="17100-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="17100-200">IS_COMPUTED</span></span>|<span data-ttu-id="17100-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="17100-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="17100-202">Procedures</span></span>  
  
|<span data-ttu-id="17100-203">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-203">ColumnName</span></span>|<span data-ttu-id="17100-204">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="17100-206">String</span><span class="sxs-lookup"><span data-stu-id="17100-206">String</span></span>|  
|<span data-ttu-id="17100-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="17100-208">String</span><span class="sxs-lookup"><span data-stu-id="17100-208">String</span></span>|  
|<span data-ttu-id="17100-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="17100-210">String</span><span class="sxs-lookup"><span data-stu-id="17100-210">String</span></span>|  
|<span data-ttu-id="17100-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="17100-212">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-212">Int16</span></span>|  
|<span data-ttu-id="17100-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="17100-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="17100-214">String</span><span class="sxs-lookup"><span data-stu-id="17100-214">String</span></span>|  
|<span data-ttu-id="17100-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-215">DESCRIPTION</span></span>|<span data-ttu-id="17100-216">String</span><span class="sxs-lookup"><span data-stu-id="17100-216">String</span></span>|  
|<span data-ttu-id="17100-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="17100-217">DATE_CREATED</span></span>|<span data-ttu-id="17100-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-218">DateTime</span></span>|  
|<span data-ttu-id="17100-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="17100-219">DATE_MODIFIED</span></span>|<span data-ttu-id="17100-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="17100-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="17100-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="17100-222">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-222">ColumnName</span></span>|<span data-ttu-id="17100-223">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="17100-225">String</span><span class="sxs-lookup"><span data-stu-id="17100-225">String</span></span>|  
|<span data-ttu-id="17100-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="17100-227">String</span><span class="sxs-lookup"><span data-stu-id="17100-227">String</span></span>|  
|<span data-ttu-id="17100-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="17100-229">String</span><span class="sxs-lookup"><span data-stu-id="17100-229">String</span></span>|  
|<span data-ttu-id="17100-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-230">PARAMETER_NAME</span></span>|<span data-ttu-id="17100-231">String</span><span class="sxs-lookup"><span data-stu-id="17100-231">String</span></span>|  
|<span data-ttu-id="17100-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="17100-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="17100-233">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-233">Int32</span></span>|  
|<span data-ttu-id="17100-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="17100-235">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-235">Int32</span></span>|  
|<span data-ttu-id="17100-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="17100-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="17100-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-237">Boolean</span></span>|  
|<span data-ttu-id="17100-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="17100-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="17100-239">String</span><span class="sxs-lookup"><span data-stu-id="17100-239">String</span></span>|  
|<span data-ttu-id="17100-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="17100-240">IS_NULLABLE</span></span>|<span data-ttu-id="17100-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-241">Boolean</span></span>|  
|<span data-ttu-id="17100-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-242">DATA_TYPE</span></span>|<span data-ttu-id="17100-243">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-243">Int32</span></span>|  
|<span data-ttu-id="17100-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="17100-245">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-245">Int64</span></span>|  
|<span data-ttu-id="17100-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="17100-247">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-247">Int64</span></span>|  
|<span data-ttu-id="17100-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="17100-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="17100-249">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-249">Int32</span></span>|  
|<span data-ttu-id="17100-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="17100-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="17100-251">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-251">Int16</span></span>|  
|<span data-ttu-id="17100-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-252">DESCRIPTION</span></span>|<span data-ttu-id="17100-253">String</span><span class="sxs-lookup"><span data-stu-id="17100-253">String</span></span>|  
|<span data-ttu-id="17100-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-254">TYPE_NAME</span></span>|<span data-ttu-id="17100-255">String</span><span class="sxs-lookup"><span data-stu-id="17100-255">String</span></span>|  
|<span data-ttu-id="17100-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="17100-257">String</span><span class="sxs-lookup"><span data-stu-id="17100-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="17100-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="17100-258">Catalog</span></span>  
  
|<span data-ttu-id="17100-259">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-259">ColumnName</span></span>|<span data-ttu-id="17100-260">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-261">CATALOG_NAME</span></span>|<span data-ttu-id="17100-262">String</span><span class="sxs-lookup"><span data-stu-id="17100-262">String</span></span>|  
|<span data-ttu-id="17100-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-263">DESCRIPTION</span></span>|<span data-ttu-id="17100-264">String</span><span class="sxs-lookup"><span data-stu-id="17100-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="17100-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="17100-265">Indexes</span></span>  
  
|<span data-ttu-id="17100-266">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-266">ColumnName</span></span>|<span data-ttu-id="17100-267">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-268">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-269">String</span><span class="sxs-lookup"><span data-stu-id="17100-269">String</span></span>|  
|<span data-ttu-id="17100-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-271">String</span><span class="sxs-lookup"><span data-stu-id="17100-271">String</span></span>|  
|<span data-ttu-id="17100-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-272">TABLE_NAME</span></span>|<span data-ttu-id="17100-273">String</span><span class="sxs-lookup"><span data-stu-id="17100-273">String</span></span>|  
|<span data-ttu-id="17100-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-274">INDEX_CATALOG</span></span>|<span data-ttu-id="17100-275">String</span><span class="sxs-lookup"><span data-stu-id="17100-275">String</span></span>|  
|<span data-ttu-id="17100-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="17100-277">String</span><span class="sxs-lookup"><span data-stu-id="17100-277">String</span></span>|  
|<span data-ttu-id="17100-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-278">INDEX_NAME</span></span>|<span data-ttu-id="17100-279">String</span><span class="sxs-lookup"><span data-stu-id="17100-279">String</span></span>|  
|<span data-ttu-id="17100-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="17100-280">PRIMARY_KEY</span></span>|<span data-ttu-id="17100-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-281">Boolean</span></span>|  
|<span data-ttu-id="17100-282">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="17100-282">UNIQUE</span></span>|<span data-ttu-id="17100-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-283">Boolean</span></span>|  
|<span data-ttu-id="17100-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="17100-284">CLUSTERED</span></span>|<span data-ttu-id="17100-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-285">Boolean</span></span>|  
|<span data-ttu-id="17100-286">TYP</span><span class="sxs-lookup"><span data-stu-id="17100-286">TYPE</span></span>|<span data-ttu-id="17100-287">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-287">Int32</span></span>|  
|<span data-ttu-id="17100-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="17100-288">FILL_FACTOR</span></span>|<span data-ttu-id="17100-289">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-289">Int32</span></span>|  
|<span data-ttu-id="17100-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="17100-290">INITIAL_SIZE</span></span>|<span data-ttu-id="17100-291">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-291">Int32</span></span>|  
|<span data-ttu-id="17100-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="17100-292">NULLS</span></span>|<span data-ttu-id="17100-293">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-293">Int32</span></span>|  
|<span data-ttu-id="17100-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="17100-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="17100-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-295">Boolean</span></span>|  
|<span data-ttu-id="17100-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="17100-296">AUTO_UPDATE</span></span>|<span data-ttu-id="17100-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-297">Boolean</span></span>|  
|<span data-ttu-id="17100-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="17100-298">NULL_COLLATION</span></span>|<span data-ttu-id="17100-299">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-299">Int32</span></span>|  
|<span data-ttu-id="17100-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="17100-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="17100-301">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-301">Int64</span></span>|  
|<span data-ttu-id="17100-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-302">COLUMN_NAME</span></span>|<span data-ttu-id="17100-303">String</span><span class="sxs-lookup"><span data-stu-id="17100-303">String</span></span>|  
|<span data-ttu-id="17100-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-304">COLUMN_GUID</span></span>|<span data-ttu-id="17100-305">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-305">Guid</span></span>|  
|<span data-ttu-id="17100-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-306">COLUMN_PROPID</span></span>|<span data-ttu-id="17100-307">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-307">Int64</span></span>|  
|<span data-ttu-id="17100-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="17100-308">COLLATION</span></span>|<span data-ttu-id="17100-309">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-309">Int16</span></span>|  
|<span data-ttu-id="17100-310">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="17100-310">CARDINALITY</span></span>|<span data-ttu-id="17100-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="17100-311">Decimal</span></span>|  
|<span data-ttu-id="17100-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="17100-312">PAGES</span></span>|<span data-ttu-id="17100-313">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-313">Int32</span></span>|  
|<span data-ttu-id="17100-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="17100-314">FILTER_CONDITION</span></span>|<span data-ttu-id="17100-315">String</span><span class="sxs-lookup"><span data-stu-id="17100-315">String</span></span>|  
|<span data-ttu-id="17100-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="17100-316">INTEGRATED</span></span>|<span data-ttu-id="17100-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="17100-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="17100-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="17100-319">Oracle OLE DB ovladače Microsoft podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="17100-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="17100-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="17100-320">Tables</span></span>  
  
-   <span data-ttu-id="17100-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="17100-321">Columns</span></span>  
  
-   <span data-ttu-id="17100-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="17100-322">Procedures</span></span>  
  
-   <span data-ttu-id="17100-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="17100-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="17100-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="17100-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="17100-325">zobrazení</span><span class="sxs-lookup"><span data-stu-id="17100-325">Views</span></span>  
  
-   <span data-ttu-id="17100-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="17100-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="17100-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="17100-327">Tables</span></span>  
  
|<span data-ttu-id="17100-328">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-328">ColumnName</span></span>|<span data-ttu-id="17100-329">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-330">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-331">String</span><span class="sxs-lookup"><span data-stu-id="17100-331">String</span></span>|  
|<span data-ttu-id="17100-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-333">String</span><span class="sxs-lookup"><span data-stu-id="17100-333">String</span></span>|  
|<span data-ttu-id="17100-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-334">TABLE_NAME</span></span>|<span data-ttu-id="17100-335">String</span><span class="sxs-lookup"><span data-stu-id="17100-335">String</span></span>|  
|<span data-ttu-id="17100-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-336">TABLE_TYPE</span></span>|<span data-ttu-id="17100-337">String</span><span class="sxs-lookup"><span data-stu-id="17100-337">String</span></span>|  
|<span data-ttu-id="17100-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-338">TABLE_GUID</span></span>|<span data-ttu-id="17100-339">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-339">Guid</span></span>|  
|<span data-ttu-id="17100-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-340">DESCRIPTION</span></span>|<span data-ttu-id="17100-341">String</span><span class="sxs-lookup"><span data-stu-id="17100-341">String</span></span>|  
|<span data-ttu-id="17100-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-342">TABLE_PROPID</span></span>|<span data-ttu-id="17100-343">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-343">Int64</span></span>|  
|<span data-ttu-id="17100-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="17100-344">DATE_CREATED</span></span>|<span data-ttu-id="17100-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-345">DateTime</span></span>|  
|<span data-ttu-id="17100-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="17100-346">DATE_MODIFIED</span></span>|<span data-ttu-id="17100-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="17100-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="17100-348">Columns</span></span>  
  
|<span data-ttu-id="17100-349">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-349">ColumnName</span></span>|<span data-ttu-id="17100-350">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-351">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-352">String</span><span class="sxs-lookup"><span data-stu-id="17100-352">String</span></span>|  
|<span data-ttu-id="17100-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-354">String</span><span class="sxs-lookup"><span data-stu-id="17100-354">String</span></span>|  
|<span data-ttu-id="17100-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-355">TABLE_NAME</span></span>|<span data-ttu-id="17100-356">String</span><span class="sxs-lookup"><span data-stu-id="17100-356">String</span></span>|  
|<span data-ttu-id="17100-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-357">COLUMN_NAME</span></span>|<span data-ttu-id="17100-358">String</span><span class="sxs-lookup"><span data-stu-id="17100-358">String</span></span>|  
|<span data-ttu-id="17100-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-359">COLUMN_GUID</span></span>|<span data-ttu-id="17100-360">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-360">Guid</span></span>|  
|<span data-ttu-id="17100-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-361">COLUMN_PROPID</span></span>|<span data-ttu-id="17100-362">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-362">Int64</span></span>|  
|<span data-ttu-id="17100-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="17100-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="17100-364">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-364">Int64</span></span>|  
|<span data-ttu-id="17100-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="17100-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="17100-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-366">Boolean</span></span>|  
|<span data-ttu-id="17100-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="17100-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="17100-368">String</span><span class="sxs-lookup"><span data-stu-id="17100-368">String</span></span>|  
|<span data-ttu-id="17100-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="17100-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="17100-370">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-370">Int64</span></span>|  
|<span data-ttu-id="17100-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="17100-371">IS_NULLABLE</span></span>|<span data-ttu-id="17100-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-372">Boolean</span></span>|  
|<span data-ttu-id="17100-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-373">DATA_TYPE</span></span>|<span data-ttu-id="17100-374">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-374">Int32</span></span>|  
|<span data-ttu-id="17100-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-375">TYPE_GUID</span></span>|<span data-ttu-id="17100-376">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-376">Guid</span></span>|  
|<span data-ttu-id="17100-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="17100-378">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-378">Int64</span></span>|  
|<span data-ttu-id="17100-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="17100-380">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-380">Int64</span></span>|  
|<span data-ttu-id="17100-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="17100-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="17100-382">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-382">Int32</span></span>|  
|<span data-ttu-id="17100-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="17100-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="17100-384">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-384">Int16</span></span>|  
|<span data-ttu-id="17100-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="17100-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="17100-386">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-386">Int64</span></span>|  
|<span data-ttu-id="17100-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="17100-388">String</span><span class="sxs-lookup"><span data-stu-id="17100-388">String</span></span>|  
|<span data-ttu-id="17100-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="17100-390">String</span><span class="sxs-lookup"><span data-stu-id="17100-390">String</span></span>|  
|<span data-ttu-id="17100-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="17100-392">String</span><span class="sxs-lookup"><span data-stu-id="17100-392">String</span></span>|  
|<span data-ttu-id="17100-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="17100-394">String</span><span class="sxs-lookup"><span data-stu-id="17100-394">String</span></span>|  
|<span data-ttu-id="17100-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="17100-396">String</span><span class="sxs-lookup"><span data-stu-id="17100-396">String</span></span>|  
|<span data-ttu-id="17100-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-397">COLLATION_NAME</span></span>|<span data-ttu-id="17100-398">String</span><span class="sxs-lookup"><span data-stu-id="17100-398">String</span></span>|  
|<span data-ttu-id="17100-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="17100-400">String</span><span class="sxs-lookup"><span data-stu-id="17100-400">String</span></span>|  
|<span data-ttu-id="17100-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="17100-402">String</span><span class="sxs-lookup"><span data-stu-id="17100-402">String</span></span>|  
|<span data-ttu-id="17100-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-403">DOMAIN_NAME</span></span>|<span data-ttu-id="17100-404">String</span><span class="sxs-lookup"><span data-stu-id="17100-404">String</span></span>|  
|<span data-ttu-id="17100-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-405">DESCRIPTION</span></span>|<span data-ttu-id="17100-406">String</span><span class="sxs-lookup"><span data-stu-id="17100-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="17100-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="17100-407">Procedures</span></span>  
  
|<span data-ttu-id="17100-408">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-408">ColumnName</span></span>|<span data-ttu-id="17100-409">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="17100-411">String</span><span class="sxs-lookup"><span data-stu-id="17100-411">String</span></span>|  
|<span data-ttu-id="17100-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="17100-413">String</span><span class="sxs-lookup"><span data-stu-id="17100-413">String</span></span>|  
|<span data-ttu-id="17100-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="17100-415">String</span><span class="sxs-lookup"><span data-stu-id="17100-415">String</span></span>|  
|<span data-ttu-id="17100-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="17100-417">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-417">Int16</span></span>|  
|<span data-ttu-id="17100-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="17100-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="17100-419">String</span><span class="sxs-lookup"><span data-stu-id="17100-419">String</span></span>|  
|<span data-ttu-id="17100-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-420">DESCRIPTION</span></span>|<span data-ttu-id="17100-421">String</span><span class="sxs-lookup"><span data-stu-id="17100-421">String</span></span>|  
|<span data-ttu-id="17100-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="17100-422">DATE_CREATED</span></span>|<span data-ttu-id="17100-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-423">DateTime</span></span>|  
|<span data-ttu-id="17100-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="17100-424">DATE_MODIFIED</span></span>|<span data-ttu-id="17100-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="17100-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="17100-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="17100-427">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-427">ColumnName</span></span>|<span data-ttu-id="17100-428">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="17100-430">String</span><span class="sxs-lookup"><span data-stu-id="17100-430">String</span></span>|  
|<span data-ttu-id="17100-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="17100-432">String</span><span class="sxs-lookup"><span data-stu-id="17100-432">String</span></span>|  
|<span data-ttu-id="17100-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="17100-434">String</span><span class="sxs-lookup"><span data-stu-id="17100-434">String</span></span>|  
|<span data-ttu-id="17100-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-435">COLUMN_NAME</span></span>|<span data-ttu-id="17100-436">String</span><span class="sxs-lookup"><span data-stu-id="17100-436">String</span></span>|  
|<span data-ttu-id="17100-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-437">COLUMN_GUID</span></span>|<span data-ttu-id="17100-438">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-438">Guid</span></span>|  
|<span data-ttu-id="17100-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-439">COLUMN_PROPID</span></span>|<span data-ttu-id="17100-440">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-440">Int64</span></span>|  
|<span data-ttu-id="17100-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="17100-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="17100-442">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-442">Int64</span></span>|  
|<span data-ttu-id="17100-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="17100-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="17100-444">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-444">Int64</span></span>|  
|<span data-ttu-id="17100-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="17100-445">IS_NULLABLE</span></span>|<span data-ttu-id="17100-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-446">Boolean</span></span>|  
|<span data-ttu-id="17100-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-447">DATA_TYPE</span></span>|<span data-ttu-id="17100-448">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-448">Int32</span></span>|  
|<span data-ttu-id="17100-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-449">TYPE_GUID</span></span>|<span data-ttu-id="17100-450">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-450">Guid</span></span>|  
|<span data-ttu-id="17100-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="17100-452">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-452">Int64</span></span>|  
|<span data-ttu-id="17100-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="17100-454">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-454">Int64</span></span>|  
|<span data-ttu-id="17100-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="17100-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="17100-456">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-456">Int32</span></span>|  
|<span data-ttu-id="17100-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="17100-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="17100-458">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-458">Int16</span></span>|  
|<span data-ttu-id="17100-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-459">DESCRIPTION</span></span>|<span data-ttu-id="17100-460">String</span><span class="sxs-lookup"><span data-stu-id="17100-460">String</span></span>|  
|<span data-ttu-id="17100-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="17100-461">OVERLOAD</span></span>|<span data-ttu-id="17100-462">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="17100-463">zobrazení</span><span class="sxs-lookup"><span data-stu-id="17100-463">Views</span></span>  
  
|<span data-ttu-id="17100-464">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-464">ColumnName</span></span>|<span data-ttu-id="17100-465">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-466">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-467">String</span><span class="sxs-lookup"><span data-stu-id="17100-467">String</span></span>|  
|<span data-ttu-id="17100-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-469">String</span><span class="sxs-lookup"><span data-stu-id="17100-469">String</span></span>|  
|<span data-ttu-id="17100-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-470">TABLE_NAME</span></span>|<span data-ttu-id="17100-471">String</span><span class="sxs-lookup"><span data-stu-id="17100-471">String</span></span>|  
|<span data-ttu-id="17100-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="17100-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="17100-473">String</span><span class="sxs-lookup"><span data-stu-id="17100-473">String</span></span>|  
|<span data-ttu-id="17100-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="17100-474">CHECK_OPTION</span></span>|<span data-ttu-id="17100-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-475">Boolean</span></span>|  
|<span data-ttu-id="17100-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="17100-476">IS_UPDATABLE</span></span>|<span data-ttu-id="17100-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-477">Boolean</span></span>|  
|<span data-ttu-id="17100-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-478">DESCRIPTION</span></span>|<span data-ttu-id="17100-479">String</span><span class="sxs-lookup"><span data-stu-id="17100-479">String</span></span>|  
|<span data-ttu-id="17100-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="17100-480">DATE_CREATED</span></span>|<span data-ttu-id="17100-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-481">DateTime</span></span>|  
|<span data-ttu-id="17100-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="17100-482">DATE_MODIFIED</span></span>|<span data-ttu-id="17100-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="17100-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="17100-484">Indexes</span></span>  
  
|<span data-ttu-id="17100-485">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-485">ColumnName</span></span>|<span data-ttu-id="17100-486">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-487">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-488">String</span><span class="sxs-lookup"><span data-stu-id="17100-488">String</span></span>|  
|<span data-ttu-id="17100-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-490">String</span><span class="sxs-lookup"><span data-stu-id="17100-490">String</span></span>|  
|<span data-ttu-id="17100-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-491">TABLE_NAME</span></span>|<span data-ttu-id="17100-492">String</span><span class="sxs-lookup"><span data-stu-id="17100-492">String</span></span>|  
|<span data-ttu-id="17100-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-493">INDEX_CATALOG</span></span>|<span data-ttu-id="17100-494">String</span><span class="sxs-lookup"><span data-stu-id="17100-494">String</span></span>|  
|<span data-ttu-id="17100-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="17100-496">String</span><span class="sxs-lookup"><span data-stu-id="17100-496">String</span></span>|  
|<span data-ttu-id="17100-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-497">INDEX_NAME</span></span>|<span data-ttu-id="17100-498">String</span><span class="sxs-lookup"><span data-stu-id="17100-498">String</span></span>|  
|<span data-ttu-id="17100-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="17100-499">PRIMARY_KEY</span></span>|<span data-ttu-id="17100-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-500">Boolean</span></span>|  
|<span data-ttu-id="17100-501">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="17100-501">UNIQUE</span></span>|<span data-ttu-id="17100-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-502">Boolean</span></span>|  
|<span data-ttu-id="17100-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="17100-503">CLUSTERED</span></span>|<span data-ttu-id="17100-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-504">Boolean</span></span>|  
|<span data-ttu-id="17100-505">TYP</span><span class="sxs-lookup"><span data-stu-id="17100-505">TYPE</span></span>|<span data-ttu-id="17100-506">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-506">Int32</span></span>|  
|<span data-ttu-id="17100-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="17100-507">FILL_FACTOR</span></span>|<span data-ttu-id="17100-508">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-508">Int32</span></span>|  
|<span data-ttu-id="17100-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="17100-509">INITIAL_SIZE</span></span>|<span data-ttu-id="17100-510">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-510">Int32</span></span>|  
|<span data-ttu-id="17100-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="17100-511">NULLS</span></span>|<span data-ttu-id="17100-512">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-512">Int32</span></span>|  
|<span data-ttu-id="17100-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="17100-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="17100-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-514">Boolean</span></span>|  
|<span data-ttu-id="17100-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="17100-515">AUTO_UPDATE</span></span>|<span data-ttu-id="17100-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-516">Boolean</span></span>|  
|<span data-ttu-id="17100-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="17100-517">NULL_COLLATION</span></span>|<span data-ttu-id="17100-518">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-518">Int32</span></span>|  
|<span data-ttu-id="17100-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="17100-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="17100-520">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-520">Int64</span></span>|  
|<span data-ttu-id="17100-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-521">COLUMN_NAME</span></span>|<span data-ttu-id="17100-522">String</span><span class="sxs-lookup"><span data-stu-id="17100-522">String</span></span>|  
|<span data-ttu-id="17100-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-523">COLUMN_GUID</span></span>|<span data-ttu-id="17100-524">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-524">Guid</span></span>|  
|<span data-ttu-id="17100-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-525">COLUMN_PROPID</span></span>|<span data-ttu-id="17100-526">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-526">Int64</span></span>|  
|<span data-ttu-id="17100-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="17100-527">COLLATION</span></span>|<span data-ttu-id="17100-528">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-528">Int16</span></span>|  
|<span data-ttu-id="17100-529">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="17100-529">CARDINALITY</span></span>|<span data-ttu-id="17100-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="17100-530">Decimal</span></span>|  
|<span data-ttu-id="17100-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="17100-531">PAGES</span></span>|<span data-ttu-id="17100-532">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-532">Int32</span></span>|  
|<span data-ttu-id="17100-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="17100-533">FILTER_CONDITION</span></span>|<span data-ttu-id="17100-534">String</span><span class="sxs-lookup"><span data-stu-id="17100-534">String</span></span>|  
|<span data-ttu-id="17100-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="17100-535">INTEGRATED</span></span>|<span data-ttu-id="17100-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="17100-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="17100-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="17100-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="17100-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="17100-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="17100-539">Tables</span></span>  
  
-   <span data-ttu-id="17100-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="17100-540">Columns</span></span>  
  
-   <span data-ttu-id="17100-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="17100-541">Procedures</span></span>  
  
-   <span data-ttu-id="17100-542">zobrazení</span><span class="sxs-lookup"><span data-stu-id="17100-542">Views</span></span>  
  
-   <span data-ttu-id="17100-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="17100-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="17100-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="17100-544">Tables</span></span>  
  
|<span data-ttu-id="17100-545">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-545">ColumnName</span></span>|<span data-ttu-id="17100-546">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-547">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-548">String</span><span class="sxs-lookup"><span data-stu-id="17100-548">String</span></span>|  
|<span data-ttu-id="17100-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-550">String</span><span class="sxs-lookup"><span data-stu-id="17100-550">String</span></span>|  
|<span data-ttu-id="17100-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-551">TABLE_NAME</span></span>|<span data-ttu-id="17100-552">String</span><span class="sxs-lookup"><span data-stu-id="17100-552">String</span></span>|  
|<span data-ttu-id="17100-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-553">TABLE_TYPE</span></span>|<span data-ttu-id="17100-554">String</span><span class="sxs-lookup"><span data-stu-id="17100-554">String</span></span>|  
|<span data-ttu-id="17100-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-555">TABLE_GUID</span></span>|<span data-ttu-id="17100-556">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-556">Guid</span></span>|  
|<span data-ttu-id="17100-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-557">DESCRIPTION</span></span>|<span data-ttu-id="17100-558">String</span><span class="sxs-lookup"><span data-stu-id="17100-558">String</span></span>|  
|<span data-ttu-id="17100-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-559">TABLE_PROPID</span></span>|<span data-ttu-id="17100-560">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-560">Int64</span></span>|  
|<span data-ttu-id="17100-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="17100-561">DATE_CREATED</span></span>|<span data-ttu-id="17100-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-562">DateTime</span></span>|  
|<span data-ttu-id="17100-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="17100-563">DATE_MODIFIED</span></span>|<span data-ttu-id="17100-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="17100-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="17100-565">Columns</span></span>  
  
|<span data-ttu-id="17100-566">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-566">ColumnName</span></span>|<span data-ttu-id="17100-567">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-568">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-569">String</span><span class="sxs-lookup"><span data-stu-id="17100-569">String</span></span>|  
|<span data-ttu-id="17100-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-571">String</span><span class="sxs-lookup"><span data-stu-id="17100-571">String</span></span>|  
|<span data-ttu-id="17100-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-572">TABLE_NAME</span></span>|<span data-ttu-id="17100-573">String</span><span class="sxs-lookup"><span data-stu-id="17100-573">String</span></span>|  
|<span data-ttu-id="17100-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-574">COLUMN_NAME</span></span>|<span data-ttu-id="17100-575">String</span><span class="sxs-lookup"><span data-stu-id="17100-575">String</span></span>|  
|<span data-ttu-id="17100-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-576">COLUMN_GUID</span></span>|<span data-ttu-id="17100-577">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-577">Guid</span></span>|  
|<span data-ttu-id="17100-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-578">COLUMN_PROPID</span></span>|<span data-ttu-id="17100-579">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-579">Int64</span></span>|  
|<span data-ttu-id="17100-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="17100-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="17100-581">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-581">Int64</span></span>|  
|<span data-ttu-id="17100-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="17100-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="17100-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-583">Boolean</span></span>|  
|<span data-ttu-id="17100-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="17100-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="17100-585">String</span><span class="sxs-lookup"><span data-stu-id="17100-585">String</span></span>|  
|<span data-ttu-id="17100-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="17100-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="17100-587">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-587">Int64</span></span>|  
|<span data-ttu-id="17100-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="17100-588">IS_NULLABLE</span></span>|<span data-ttu-id="17100-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-589">Boolean</span></span>|  
|<span data-ttu-id="17100-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-590">DATA_TYPE</span></span>|<span data-ttu-id="17100-591">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-591">Int32</span></span>|  
|<span data-ttu-id="17100-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-592">TYPE_GUID</span></span>|<span data-ttu-id="17100-593">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-593">Guid</span></span>|  
|<span data-ttu-id="17100-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="17100-595">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-595">Int64</span></span>|  
|<span data-ttu-id="17100-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="17100-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="17100-597">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-597">Int64</span></span>|  
|<span data-ttu-id="17100-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="17100-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="17100-599">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-599">Int32</span></span>|  
|<span data-ttu-id="17100-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="17100-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="17100-601">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-601">Int16</span></span>|  
|<span data-ttu-id="17100-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="17100-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="17100-603">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-603">Int64</span></span>|  
|<span data-ttu-id="17100-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="17100-605">String</span><span class="sxs-lookup"><span data-stu-id="17100-605">String</span></span>|  
|<span data-ttu-id="17100-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="17100-607">String</span><span class="sxs-lookup"><span data-stu-id="17100-607">String</span></span>|  
|<span data-ttu-id="17100-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="17100-609">String</span><span class="sxs-lookup"><span data-stu-id="17100-609">String</span></span>|  
|<span data-ttu-id="17100-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="17100-611">String</span><span class="sxs-lookup"><span data-stu-id="17100-611">String</span></span>|  
|<span data-ttu-id="17100-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="17100-613">String</span><span class="sxs-lookup"><span data-stu-id="17100-613">String</span></span>|  
|<span data-ttu-id="17100-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-614">COLLATION_NAME</span></span>|<span data-ttu-id="17100-615">String</span><span class="sxs-lookup"><span data-stu-id="17100-615">String</span></span>|  
|<span data-ttu-id="17100-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="17100-617">String</span><span class="sxs-lookup"><span data-stu-id="17100-617">String</span></span>|  
|<span data-ttu-id="17100-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="17100-619">String</span><span class="sxs-lookup"><span data-stu-id="17100-619">String</span></span>|  
|<span data-ttu-id="17100-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-620">DOMAIN_NAME</span></span>|<span data-ttu-id="17100-621">String</span><span class="sxs-lookup"><span data-stu-id="17100-621">String</span></span>|  
|<span data-ttu-id="17100-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-622">DESCRIPTION</span></span>|<span data-ttu-id="17100-623">String</span><span class="sxs-lookup"><span data-stu-id="17100-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="17100-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="17100-624">Procedures</span></span>  
  
|<span data-ttu-id="17100-625">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-625">ColumnName</span></span>|<span data-ttu-id="17100-626">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="17100-628">String</span><span class="sxs-lookup"><span data-stu-id="17100-628">String</span></span>|  
|<span data-ttu-id="17100-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="17100-630">String</span><span class="sxs-lookup"><span data-stu-id="17100-630">String</span></span>|  
|<span data-ttu-id="17100-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="17100-632">String</span><span class="sxs-lookup"><span data-stu-id="17100-632">String</span></span>|  
|<span data-ttu-id="17100-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="17100-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="17100-634">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-634">Int16</span></span>|  
|<span data-ttu-id="17100-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="17100-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="17100-636">String</span><span class="sxs-lookup"><span data-stu-id="17100-636">String</span></span>|  
|<span data-ttu-id="17100-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-637">DESCRIPTION</span></span>|<span data-ttu-id="17100-638">String</span><span class="sxs-lookup"><span data-stu-id="17100-638">String</span></span>|  
|<span data-ttu-id="17100-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="17100-639">DATE_CREATED</span></span>|<span data-ttu-id="17100-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-640">DateTime</span></span>|  
|<span data-ttu-id="17100-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="17100-641">DATE_MODIFIED</span></span>|<span data-ttu-id="17100-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="17100-643">zobrazení</span><span class="sxs-lookup"><span data-stu-id="17100-643">Views</span></span>  
  
|<span data-ttu-id="17100-644">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-644">ColumnName</span></span>|<span data-ttu-id="17100-645">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-646">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-647">String</span><span class="sxs-lookup"><span data-stu-id="17100-647">String</span></span>|  
|<span data-ttu-id="17100-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-649">String</span><span class="sxs-lookup"><span data-stu-id="17100-649">String</span></span>|  
|<span data-ttu-id="17100-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-650">TABLE_NAME</span></span>|<span data-ttu-id="17100-651">String</span><span class="sxs-lookup"><span data-stu-id="17100-651">String</span></span>|  
|<span data-ttu-id="17100-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="17100-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="17100-653">String</span><span class="sxs-lookup"><span data-stu-id="17100-653">String</span></span>|  
|<span data-ttu-id="17100-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="17100-654">CHECK_OPTION</span></span>|<span data-ttu-id="17100-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-655">Boolean</span></span>|  
|<span data-ttu-id="17100-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="17100-656">IS_UPDATABLE</span></span>|<span data-ttu-id="17100-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-657">Boolean</span></span>|  
|<span data-ttu-id="17100-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="17100-658">DESCRIPTION</span></span>|<span data-ttu-id="17100-659">String</span><span class="sxs-lookup"><span data-stu-id="17100-659">String</span></span>|  
|<span data-ttu-id="17100-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="17100-660">DATE_CREATED</span></span>|<span data-ttu-id="17100-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-661">DateTime</span></span>|  
|<span data-ttu-id="17100-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="17100-662">DATE_MODIFIED</span></span>|<span data-ttu-id="17100-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="17100-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="17100-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="17100-664">Indexes</span></span>  
  
|<span data-ttu-id="17100-665">columnName</span><span class="sxs-lookup"><span data-stu-id="17100-665">ColumnName</span></span>|<span data-ttu-id="17100-666">Datový typ</span><span class="sxs-lookup"><span data-stu-id="17100-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="17100-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-667">TABLE_CATALOG</span></span>|<span data-ttu-id="17100-668">String</span><span class="sxs-lookup"><span data-stu-id="17100-668">String</span></span>|  
|<span data-ttu-id="17100-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="17100-670">String</span><span class="sxs-lookup"><span data-stu-id="17100-670">String</span></span>|  
|<span data-ttu-id="17100-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-671">TABLE_NAME</span></span>|<span data-ttu-id="17100-672">String</span><span class="sxs-lookup"><span data-stu-id="17100-672">String</span></span>|  
|<span data-ttu-id="17100-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="17100-673">INDEX_CATALOG</span></span>|<span data-ttu-id="17100-674">String</span><span class="sxs-lookup"><span data-stu-id="17100-674">String</span></span>|  
|<span data-ttu-id="17100-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="17100-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="17100-676">String</span><span class="sxs-lookup"><span data-stu-id="17100-676">String</span></span>|  
|<span data-ttu-id="17100-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-677">INDEX_NAME</span></span>|<span data-ttu-id="17100-678">String</span><span class="sxs-lookup"><span data-stu-id="17100-678">String</span></span>|  
|<span data-ttu-id="17100-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="17100-679">PRIMARY_KEY</span></span>|<span data-ttu-id="17100-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-680">Boolean</span></span>|  
|<span data-ttu-id="17100-681">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="17100-681">UNIQUE</span></span>|<span data-ttu-id="17100-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-682">Boolean</span></span>|  
|<span data-ttu-id="17100-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="17100-683">CLUSTERED</span></span>|<span data-ttu-id="17100-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-684">Boolean</span></span>|  
|<span data-ttu-id="17100-685">TYP</span><span class="sxs-lookup"><span data-stu-id="17100-685">TYPE</span></span>|<span data-ttu-id="17100-686">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-686">Int32</span></span>|  
|<span data-ttu-id="17100-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="17100-687">FILL_FACTOR</span></span>|<span data-ttu-id="17100-688">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-688">Int32</span></span>|  
|<span data-ttu-id="17100-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="17100-689">INITIAL_SIZE</span></span>|<span data-ttu-id="17100-690">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-690">Int32</span></span>|  
|<span data-ttu-id="17100-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="17100-691">NULLS</span></span>|<span data-ttu-id="17100-692">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-692">Int32</span></span>|  
|<span data-ttu-id="17100-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="17100-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="17100-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-694">Boolean</span></span>|  
|<span data-ttu-id="17100-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="17100-695">AUTO_UPDATE</span></span>|<span data-ttu-id="17100-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-696">Boolean</span></span>|  
|<span data-ttu-id="17100-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="17100-697">NULL_COLLATION</span></span>|<span data-ttu-id="17100-698">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-698">Int32</span></span>|  
|<span data-ttu-id="17100-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="17100-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="17100-700">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-700">Int64</span></span>|  
|<span data-ttu-id="17100-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="17100-701">COLUMN_NAME</span></span>|<span data-ttu-id="17100-702">String</span><span class="sxs-lookup"><span data-stu-id="17100-702">String</span></span>|  
|<span data-ttu-id="17100-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="17100-703">COLUMN_GUID</span></span>|<span data-ttu-id="17100-704">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="17100-704">Guid</span></span>|  
|<span data-ttu-id="17100-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="17100-705">COLUMN_PROPID</span></span>|<span data-ttu-id="17100-706">Int64</span><span class="sxs-lookup"><span data-stu-id="17100-706">Int64</span></span>|  
|<span data-ttu-id="17100-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="17100-707">COLLATION</span></span>|<span data-ttu-id="17100-708">Int16</span><span class="sxs-lookup"><span data-stu-id="17100-708">Int16</span></span>|  
|<span data-ttu-id="17100-709">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="17100-709">CARDINALITY</span></span>|<span data-ttu-id="17100-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="17100-710">Decimal</span></span>|  
|<span data-ttu-id="17100-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="17100-711">PAGES</span></span>|<span data-ttu-id="17100-712">Int32</span><span class="sxs-lookup"><span data-stu-id="17100-712">Int32</span></span>|  
|<span data-ttu-id="17100-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="17100-713">FILTER_CONDITION</span></span>|<span data-ttu-id="17100-714">String</span><span class="sxs-lookup"><span data-stu-id="17100-714">String</span></span>|  
|<span data-ttu-id="17100-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="17100-715">INTEGRATED</span></span>|<span data-ttu-id="17100-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="17100-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17100-717">Viz také</span><span class="sxs-lookup"><span data-stu-id="17100-717">See Also</span></span>  
 [<span data-ttu-id="17100-718">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="17100-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
