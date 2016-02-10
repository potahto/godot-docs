.. _class_PathFollow:

PathFollow
==========

**Inherits:** :ref:`Spatial<class_spatial>` **<** :ref:`Node<class_node>` **<** :ref:`Object<class_object>`

**Category:** Core

Brief Description
-----------------

Point sampler for a :ref:`Path<class_path>`.

Member Functions
----------------

+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| void                       | :ref:`set_offset<class_PathFollow_set_offset>`  **(** :ref:`float<class_float>` offset  **)**                         |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| :ref:`float<class_float>`  | :ref:`get_offset<class_PathFollow_get_offset>`  **(** **)** const                                                     |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| void                       | :ref:`set_h_offset<class_PathFollow_set_h_offset>`  **(** :ref:`float<class_float>` h_offset  **)**                   |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| :ref:`float<class_float>`  | :ref:`get_h_offset<class_PathFollow_get_h_offset>`  **(** **)** const                                                 |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| void                       | :ref:`set_v_offset<class_PathFollow_set_v_offset>`  **(** :ref:`float<class_float>` v_offset  **)**                   |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| :ref:`float<class_float>`  | :ref:`get_v_offset<class_PathFollow_get_v_offset>`  **(** **)** const                                                 |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| void                       | :ref:`set_unit_offset<class_PathFollow_set_unit_offset>`  **(** :ref:`float<class_float>` unit_offset  **)**          |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| :ref:`float<class_float>`  | :ref:`get_unit_offset<class_PathFollow_get_unit_offset>`  **(** **)** const                                           |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| void                       | :ref:`set_rotation_mode<class_PathFollow_set_rotation_mode>`  **(** :ref:`int<class_int>` rotation_mode  **)**        |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| :ref:`int<class_int>`      | :ref:`get_rotation_mode<class_PathFollow_get_rotation_mode>`  **(** **)** const                                       |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| void                       | :ref:`set_cubic_interpolation<class_PathFollow_set_cubic_interpolation>`  **(** :ref:`bool<class_bool>` enable  **)** |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| :ref:`bool<class_bool>`    | :ref:`get_cubic_interpolation<class_PathFollow_get_cubic_interpolation>`  **(** **)** const                           |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| void                       | :ref:`set_loop<class_PathFollow_set_loop>`  **(** :ref:`bool<class_bool>` loop  **)**                                 |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+
| :ref:`bool<class_bool>`    | :ref:`has_loop<class_PathFollow_has_loop>`  **(** **)** const                                                         |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+

Numeric Constants
-----------------

- **ROTATION_NONE** = **0** --- Forbids the PathFollow to rotate.
- **ROTATION_Y** = **1** --- Allows the PathFollow to rotate in the Y axis only.
- **ROTATION_XY** = **2** --- Allows the PathFollow to rotate in both the X, and Y axes.
- **ROTATION_XYZ** = **3** --- Allows the PathFollow to rotate in any axis.

Description
-----------

This node takes its parent :ref:`Path<class_path>`, and returns the coordinates of a point within it, given a distance from the first vertex.

It is useful for making other nodes follow a path, without coding the movement pattern. For that, the nodes must be descendants of this node. Then, when setting an offset in this node, the descendant nodes will move accordingly.

Member Function Description
---------------------------

.. _class_PathFollow_set_offset:

- void  **set_offset**  **(** :ref:`float<class_float>` offset  **)**

Sets the distance from the first vertex, measured in 3D units along the path. This sets this node's position to a point within the path.

.. _class_PathFollow_get_offset:

- :ref:`float<class_float>`  **get_offset**  **(** **)** const

Returns the distance along the path in 3D units.

.. _class_PathFollow_set_h_offset:

- void  **set_h_offset**  **(** :ref:`float<class_float>` h_offset  **)**

Moves this node in the X axis. As this node's position will be set every time its offset is set, this allows many PathFollow to share the same curve (and thus the same movement pattern), yet not return the same position for a given path offset.

A similar effect may be achieved moving the this node's descendants.

.. _class_PathFollow_get_h_offset:

- :ref:`float<class_float>`  **get_h_offset**  **(** **)** const

Returns the X displacement this node has from its parent :ref:`Path<class_path>`.

.. _class_PathFollow_set_v_offset:

- void  **set_v_offset**  **(** :ref:`float<class_float>` v_offset  **)**

Moves this node in the Y axis, for the same reasons of :ref:`set_h_offset<class_PathFollow_set_h_offset>`.

.. _class_PathFollow_get_v_offset:

- :ref:`float<class_float>`  **get_v_offset**  **(** **)** const

Returns the Y displacement this node has from its parent :ref:`Path<class_path>`.

.. _class_PathFollow_set_unit_offset:

- void  **set_unit_offset**  **(** :ref:`float<class_float>` unit_offset  **)**

Sets the distance from the first vertex, considering 0.0 as the first vertex and 1.0 as the last. This is just another way of expressing the offset within the path, as the offset supplied is multiplied internally by the path's length.

.. _class_PathFollow_get_unit_offset:

- :ref:`float<class_float>`  **get_unit_offset**  **(** **)** const

Returns the distance along the path as a number in the range 0.0 (for the first vertex) to 1.0 (for the last).

.. _class_PathFollow_set_rotation_mode:

- void  **set_rotation_mode**  **(** :ref:`int<class_int>` rotation_mode  **)**

Allows or forbids rotation on one or more axes, per the constants below.

.. _class_PathFollow_get_rotation_mode:

- :ref:`int<class_int>`  **get_rotation_mode**  **(** **)** const

Returns the rotation mode. The constants below list which axes are allowed to rotate for each mode.

.. _class_PathFollow_set_cubic_interpolation:

- void  **set_cubic_interpolation**  **(** :ref:`bool<class_bool>` enable  **)**

The points along the :ref:`Curve3D<class_curve3d>` of the :ref:`Path<class_path>` are precomputed before use, for faster calculations. The point at the requested offset is then calculated interpolating between two adjacent cached points. This may present a problem if the curve makes sharp turns, as the cached points may not follow the curve closely enough.

There are two answers to this problem: Either increase the number of cached points and increase memory consumption, or make a cubic interpolation between two points at the cost of (slightly) slower calculations.

This method controls whether the position between two cached points is interpolated linearly, or cubicly.

.. _class_PathFollow_get_cubic_interpolation:

- :ref:`bool<class_bool>`  **get_cubic_interpolation**  **(** **)** const

This method returns whether the position between two cached points (see :ref:`set_cubic_interpolation<class_PathFollow_set_cubic_interpolation>`) is interpolated linearly, or cubicly.

.. _class_PathFollow_set_loop:

- void  **set_loop**  **(** :ref:`bool<class_bool>` loop  **)**

If set, any offset outside the path's length (whether set by :ref:`set_offset<class_PathFollow_set_offset>` or :ref:`set_unit_offset<class_PathFollow_set_unit_offset>` will wrap around, instead of stopping at the ends. Set it for cyclic paths.

.. _class_PathFollow_has_loop:

- :ref:`bool<class_bool>`  **has_loop**  **(** **)** const

Returns whether this node wraps its offsets around, or truncates them to the path ends.

