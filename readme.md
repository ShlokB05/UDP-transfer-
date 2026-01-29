## Lossless UDP transfer protocol using stop and wait and ACKs.

### `sender.py` 
- `send_reliable`: Implements a sliding-window reliable sender over UDP. Sends an initial window burst, processes cumulative ACKs to slide the window and send newly-opened data, and on timeout retransmits one packet.
- `transmit_entire_window_from(left_edge)`: Sends every packet from `left_edge` up to the current `win_right_edge` and returns the next sequence number after the last byte transmitted.
- `transmit_one()`: Sends the single packet starting at `win_left_edge`.

### `stopandwait.py` (stop-and-wait)
- `send_reliable(cs, filedata, receiver_binding, win_size)`: Implements stop-and-wait reliability. Sends one packet, waits up to `RTO` for an ACK, retransmits on timeout, and advances on a valid cumulative ACK.
- `transmit_one()`: Sends the single packet starting at `win_left_edge` (used for the initial send and any retransmissions).


